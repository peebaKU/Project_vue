<template>
    <div class="container">
        <div class="row mt-3">
            <div class="row sm-4">
                
                <form>
                    <img alt="Vue logo" src="../assets/logo.png" />
                    <div class="form-group">
                        <label for="username">User Name</label>
                        <input type="text" name="username" id="username" placeholder="Enter your username" class="form-control">
                    </div>
                    <div class="form-group">
                        <label for="password">Password</label>
                        <input type="password" name="password" id="password" placeholder="Enter your password" class="form-control">
                    </div>
                    <button type="submit" class="btn btn-primary my-1">Login</button>
                </form>
            </div>
        </div>
    </div>    
</template>

<script>

export default{
    name: 'LoginForm',
    data(){
        return {}       
    },
}
</script>


