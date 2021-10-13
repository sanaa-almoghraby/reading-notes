# Hashing Passwords: One-Way Road to Security
Storing Passwords is Risky and Complex
The security strength and resilience of this model depends on how the password is stored. The most basic, but also the least secure, password storage format is cleartext.
Storing passwords in cleartext is the equivalent of writing them down in a piece of digital paper. If an attacker was to break into the database and steal the passwords table, the attacker could then access each user account. This problem is compounded by the fact that many users re-use or use variations of a single password, potentially allowing the attacker to access other services different from the one being compromised. That all sounds like a security nightmare!
# What's Hashing About?
By dictionary definition, hashing refers to "chopping something into small pieces" to make it look like a "confused mess". That definition closely applies to what hashing represents in computing.
![](https://images.ctfassets.net/23aumh6u8s0i/3xP2opDfoin34ScJZMBQB5/bd706f86ade6ad72513eea23d22b039b/encryption-flow)
![](https://images.ctfassets.net/23aumh6u8s0i/ES2U6Gx7w0yVF9Asidr26/75531c3695f09272142b543a94acc0de/hash-flow)
# Why you should use BCrypt to hash passwords
In the online world, passwords play a critical role in keeping your data and other important information safe. For this reason, ensuring your passwords remain secure is critical. If not, the consequences can be catastrophic — think the Sony hacks of 2011.
# The BCrypt Solution
BCrypt is based on the Blowfish block cipher cryptomatic algorithm and takes the form of an adaptive hash function. But why should you use it to protect your data and resources? To explain, we’re going to need to get a little technical
jBCrypt
jBCrypt is a Java™ implementation of OpenBSD's Blowfish password hashing code, as described in "A Future-Adaptable Password Scheme" by Niels Provos and David Mazières.

This system hashes passwords using a version of Bruce Schneier's Blowfish block cipher with modifications designed to raise the cost of off-line password cracking and frustrate fast hardware implementation. The computation cost of the algorithm is parametised, so it can be increased as computers get faster. The intent is to make a compromise of a password database less likely to result in an attacker gaining knowledge of the plaintext passwords (e.g. using John the Ripper).

There seems to be a lack of good password hashes for Java - the top two hits in Google (as of 2006/05/24) for "Java password hash" and "Java password encryption" both offer terrible advice: one uses an unsalted hash which allows reverse dictionary lookup of passwords and the other recommends reversible encryption, which is rarely needed and should only be used as a last resort.

### jBCrypt is licensed under a ISC/BSD licence (see the LICENSE file for details) and ships with a set of JUnit unit tests to verify correct operation of the library and compatibility with the canonical C implementation of the bcrypt algorithm.

The API is very simple:

// Hash a password for the first time
String hashed = BCrypt.hashpw(password, BCrypt.gensalt());

// gensalt's log_rounds parameter determines the complexity
// the work factor is 2**log_rounds, and the default is 10
String hashed = BCrypt.hashpw(password, BCrypt.gensalt(12));

// Check that an unencrypted password matches one that has
// previously been hashed
if (BCrypt.checkpw(candidate, hashed))
	System.out.println("It matches");
else
	System.out.println("It does not match");