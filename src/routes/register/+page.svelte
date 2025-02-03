<div class="container">
    <div class="left">
<img src="3615781.jpg" alt="">
    </div>

    <div class="right">
        <h1 id="header">Sign up Account</h1>
        <p id="enter">Enter your personal data to create your account.</p>

        <form>
            <div class="fullname">
                <label for="firstname">First name</label>
                <label for="lastname">Last Name</label>
                <input
                    type="text"
                    placeholder="e.g Juan"
                    required
                    id="firstname"
                />

                <input
                    type="text"
                    placeholder="e.g Dela Cruz"
                    required
                    id="lastname"
                />
            </div>

            <div class="email">
                <label for="email">Email</label>
                <input
                    type="email"
                    placeholder="Enter your email"
                    required
                    autocomplete="email"
                />
            </div>

            <div class="password">
                <label for="password">Password</label>
                <input
                    type="password"
                    placeholder="Enter your password"
                    required
                />
            </div>

            <div class="confirmpassword">
                <label for="password">Confirm Password</label>
                <input
                    type="password"
                    placeholder="Comfirm your password"
                    required
                />
            </div>
        </form>

        <div class="buttons">
            <button id="signup">Sign Up</button>
            <p id="login">
                Already have an account? <a id="login" href="/">Login</a>
            </p>
        </div>
    </div>
</div>

<style>
    .container {
        display: flex;
        justify-content: center;
        /* border: 1px solid green; */
        align-items: center;
        min-width: 100vw;
        height: 100vh;
        font-family: proxima-nova, sans-serif;
        font-style: normal;
    }

    .container .right {
        height: 100%;
        width: 50%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        padding: 10%;
        color: white;
        background: rgb(0, 128, 0);
        background: linear-gradient(
            0deg,
            rgba(0, 128, 0, 1) 0%,
            rgba(255, 158, 42, 1) 100%
        );
    }

	.container .left {
		/* border: 1px solid blue; */
		width: 75%;
		img {
			max-width: 100%;
		}
	}


    .fullname {
        display: grid;
        grid-template-columns: 1fr 1fr;
        /* border: 1px solid red; */
        gap: 0rem 0.5rem;
    }

    .email,
    .password,
    .confirmpassword {
        display: flex;
        flex-direction: column;
    }

    #header,
    #enter {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    #header {
        font-size: 2rem;
        font-weight: bold;
    }

    #enter {
        padding-bottom: 5rem;
    }

    #signup {
        background-color: #008000;
        padding: 0.6rem 3rem;
        border-radius: 0.5rem;
        font-weight: bold;
        color: white;
        &:active {
            transform: scale(0.9);
        }
    }

    .buttons {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-block: 1.5rem;
        gap: 1.5rem;
    }

    input {
        display: flex;
        flex-direction: column;
        align-items: center;
        border-radius: 0.5rem;
        color: black;
    }

    #login {
        color: #ffffff;
        a {
            font-weight: bold;
        }
    }

form {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}
</style>
