<script>
	import { goto } from "$app/navigation";
	import { currentUser, pb } from "$lib/auth";
    /**
	 * @type {string}
	 */
    let username
    /**
	 * @type {string}
	 */
    let password

    async function login(){
        try{
        await pb.collection('users').authWithPassword(username, password)
        if($currentUser){
           goto("/")
        }
        }
        catch{
            console.log("authentication failed");
        }
    }
</script>

<form on:submit|preventDefault>
    <input placeholder="Username" type="text" bind:value={username}/>
    <input placeholder="Password" type="password" bind:value={password}/>
    <button on:click={login}>Log In</button>
</form>
