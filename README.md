public class EmailValidator {

    public static boolean isValidEmail(String email) {
        if (email == null || email.isEmpty()) {
            return false;
        }

        // 1. Check for the presence of '@'
        int atIndex = email.indexOf('@');
        if (atIndex == -1) {
            return false; // No '@' found
        }

        // 2. Check for the presence of '.' after '@'
        int dotIndex = email.lastIndexOf('.');
        if (dotIndex == -1 || dotIndex < atIndex) {
            return false; // No '.' after '@' or no '.' at all
        }

        // 3. Ensure there are characters before '@'
        if (atIndex == 0) {
            return false; // Email starts with '@'
        }

        // 4. Ensure there are characters between '@' and the last '.'
        if (dotIndex - atIndex <= 1) {
            return false; // No characters between '@' and '.'
        }

        // 5. Ensure there are characters after the last '.' (top-level domain)
        if (dotIndex == email.length() - 1) {
            return false; // Email ends with '.'
        }
        
        // 6. Basic check for invalid characters (e.g., spaces)
        if (email.contains(" ")) {
            return false;
        }

        return true;
    }

    public static void main(String[] args) {
        String email1 = "test@example.com";
        String email2 = "invalid-email";
        String email3 = "user@.com";
        String email4 = "@domain.com";
        String email5 = "user@domain.";
        String email6 = "user@domain.c"; // Too short TLD for a robust check, but passes basic checks
        String email7 = "user name@example.com";

        System.out.println(email1 + " is valid: " + isValidEmail(email1));
        System.out.println(email2 + " is valid: " + isValidEmail(email2));
        System.out.println(email3 + " is valid: " + isValidEmail(email3));
        System.out.println(email4 + " is valid: " + isValidEmail(email4));
        System.out.println(email5 + " is valid: " + isValidEmail(email5));
        System.out.println(email6 + " is valid: " + isValidEmail(email6));
        System.out.println(email7 + " is valid: " + isValidEmail(email7));
    }returnturn
