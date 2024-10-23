<h1>Express Authentication template</h1>

<p>A nodejs and express authentication template with protected routes, email verifications, password reset, admin access etc using JWT web token.</p>

<h2>Routes</h2>

router.post("/register", registerUser);
router.post("/login", loginUser);
router.get("/logout", logoutUser);
router.get("/user", protect, getUser);
router.patch("/user", protect, updateUser);

// admin route
router.delete("/admin/users/:id", protect, adminMiddleware, deleteUser);

// get all users
router.get("/admin/users", protect, creatorMiddleware, getAllUsers);

// login status
router.get("/login-status", userLoginStatus);

// email verification
router.post("/verify-email", protect, verifyEmail);

// veriify user --> email verification
router.post("/verify-user/:verificationToken", verifyUser);

// forgot password
router.post("/forgot-password", forgotPassword);

//reset password
router.post("/reset-password/:resetPasswordToken", resetPassword);

// change password ---> user must be logged in
router.patch("/change-password", protect, changePassword);
