1. Димитар Стојков 213112
2. ![cfg](https://github.com/dimniks/SI_2023_lab2_213112/assets/108998306/e2cb3c11-17f9-4059-b4b6-1817db550541)
3. Цикломатската комплексност на графот е 12. Тоа го добив преку броењето на регионите. Има вкупно 11 внатрешни и уште еден од надвор, тоа се вкупно 12 региони.
4. @Test
    void testFunctionValidUser() {
        User user = new User("janko", "Lozink@@", "jan@ko.com");
        List<User> allUsers = new ArrayList<>();
        allUsers.add(new User("jule", "pass123", "ju@le.com"));

        boolean result = SILab2.function(user, allUsers);

        Assertions.assertTrue(result, "true");
    }

testFunctionValidUser: Овој тест случај проверува дали function() враќа точно за валиден корисник со единствена е-пошта и лозинка што ги исполнува критериумите.

    @Test
    void testFunctionNullUser() {
        User user = null;
        List<User> allUsers = new ArrayList<>();
        allUsers.add(new User("jule", "pass123", "ju@le.com"));

        Assertions.assertThrows(RuntimeException.class, () -> SILab2.function(user, allUsers),
                "ERuntimeException za null korisnik");
    }

testFunctionNullUser: Овој тест случај потврдува дека function() фрла RuntimeException кога корисникот е нула, како што се очекуваше.

    @Test
    void testFunctionNullPassword() {
        User user = new User("janko", null, "jan@ko.com");
        List<User> allUsers = new ArrayList<>();
        allUsers.add(new User("jule", "pass123", "ju@le.com"));

        Assertions.assertThrows(RuntimeException.class, () -> SILab2.function(user, allUsers),
                "RuntimeException za null password");
    }

testFunctionNullPassword: Овој тест случај осигурува дека function() фрла RuntimeException кога лозинката е нула.

    @Test
    void testFunctionNullEmail() {
        User user = new User("janko", "Lozink@@", null);
        List<User> allUsers = new ArrayList<>();
        allUsers.add(new User("jule", "pass123", "ju@le.com"));

        Assertions.assertThrows(RuntimeException.class, () -> SILab2.function(user, allUsers),
                "RuntimeException za null email");
    }

testFunctionNullEmail: Овој тест случај потврдува дека function() фрла RuntimeException кога е-поштата е нула.

    @Test
    void testFunctionNullUsername() {
        User user = new User(null, "Lozink@@", "jan@ko.com");
        List<User> allUsers = new ArrayList<>();
        allUsers.add(new User("jule", "pass123", "ju@le.com"));

        boolean result = SILab2.function(user, allUsers);

        Assertions.assertEquals(user.getEmail(), user.getUsername(),
                "username isto kako email koga e null");
        Assertions.assertFalse(result, "vrakja false koga username e null");
    }

testFunctionNullUsername: Овој тест случај потврдува дали function() го поставува корисничкото име како е-пошта кога корисничкото име е нула, а исто така проверува дали враќа неточно во овој случај.

    @Test
    void testFunctionInvalidPassword() {
        User user = new User("", "password", "jan@ko.com");
        List<User> allUsers = new ArrayList<>();
        allUsers.add(new User("jule", "pass123", "ju@le.com"));

        boolean result = SILab2.function(user, allUsers);

        Assertions.assertFalse(result, "vrakja false za nevalidna lozinka");
    }

testFunctionInvalidPassword: Овој тест случај го тестира сценариото каде лозинката е празна и очекува методот на function() да врати неточно.

    @Test
    void testFunctionInvalidEmail() {
        User user = new User("janko", "Lozink@@", "janko.com");
        List<User> allUsers = new ArrayList<>();
        allUsers.add(new User("jule", "pass123", "ju@le.com"));

        boolean result = SILab2.function(user, allUsers);

        Assertions.assertFalse(result, "vrakja false za nevaliden email");
    }

testFunctionInvalidEmail: Овој тест случај проверува дали function() враќа false за неважечка е-пошта што не го содржи симболот „@“.

    @Test
    void testFunctionExistingUser() {
        User user = new User("janko", "Lozink@@", "jan@ko.com");
        List<User> allUsers = new ArrayList<>();
        allUsers.add(new User("janko", "pass123", "ju@le.com"));

        boolean result = SILab2.function(user, allUsers);

        Assertions.assertFalse(result, "vrakja false za postoechki korisnik");
    }

testFunctionExistingUser: Овој тест случај потврдува дека function() враќа false кога корисничкото име или е-поштата на корисникот веќе постојат во списокот со сите корисници.

    @Test
    void testFunctionSpecialCharacters() {
        User user = new User("janko", "Lozink@@", "jan@ko.com");
        List<User> allUsers = new ArrayList<>();

        boolean result = SILab2.function(user, allUsers);

        Assertions.assertFalse(result, "vrakja false, bidejki lozinkata nema specijalni karakteri");
    }

testFunctionSpecialCharacters: Овој тест случај осигурува дека function() враќа false кога лозинката на корисникот не содржи никакви специјални знаци.
5. @Test
    void testFunctionNullUser() {
        User user = null;
        List<User> allUsers = new ArrayList<>();

        Assertions.assertThrows(RuntimeException.class, () -> SILab2.function(user, allUsers),
                "RuntimeException za null user");
    }

testFunctionNullUser: Овој тест случај потврдува дека function() фрла RuntimeException кога корисникот е нула, како што се очекуваше.

    @Test
    void testFunctionNullPassword() {
        User user = new User("janko", null, "jan@ko.com");
        List<User> allUsers = new ArrayList<>();

        Assertions.assertThrows(RuntimeException.class, () -> SILab2.function(user, allUsers),
                "RuntimeException za null password");
    }

testFunctionNullPassword: Овој тест случај осигурува дека function() фрла RuntimeException кога лозинката е нула.

    @Test
    void testFunctionNullEmail() {
        User user = new User("janko", "Lozink@@", null);
        List<User> allUsers = new ArrayList<>();

        Assertions.assertThrows(RuntimeException.class, () -> SILab2.function(user, allUsers),
                "RuntimeException za null email");
    }

testFunctionNullEmail: Овој тест случај потврдува дека function() фрла RuntimeException кога е-поштата е нула.

    @Test
    void testFunctionNullUserPassword() {
        User user = null;
        List<User> allUsers = new ArrayList<>();
        allUsers.add(new User("jule", "pass123", "ju@le.com"));

        Assertions.assertThrows(RuntimeException.class, () -> SILab2.function(user, allUsers),
                "RuntimeException za null user i password");
    }

testFunctionNullUserPassword: Овој тест случај проверува дали function() фрла RuntimeException кога и корисникот и лозинката се нула.

    @Test
    void testFunctionNullUserEmail() {
        User user = null;
        List<User> allUsers = new ArrayList<>();
        allUsers.add(new User("jule", "pass123", "ju@le.com"));

        Assertions.assertThrows(RuntimeException.class, () -> SILab2.function(user, allUsers),
                "RuntimeException za null user i email");
    }

testFunctionNullUserEmail: Овој тест случај потврдува дека function() фрла RuntimeException кога и корисникот и е-поштата се нула.

    @Test
    void testFunctionNullPasswordEmail() {
        User user = new User("janko", null, null);
        List<User> allUsers = new ArrayList<>();

        Assertions.assertThrows(RuntimeException.class, () -> SILab2.function(user, allUsers),
                "RuntimeException za null password i email");
    }

testFunctionNullPasswordEmail: Овој тест случај осигурува дека function() фрла RuntimeException кога и лозинката и е-поштата се нула.

    @Test
    void testFunctionNullUserPasswordEmail() {
        User user = null;
        List<User> allUsers = new ArrayList<>();

        Assertions.assertThrows(RuntimeException.class, () -> SILab2.function(user, allUsers),
                "RuntimeException za null user, password, i email");
    }

testFunctionNullUserPasswordEmail: Овој тест случај потврдува дека function() фрла RuntimeException кога корисникот, лозинката и е-поштата се сите нула.

    @Test
    void testFunctionValidUser() {
        User user = new User("janko", "Lozink@@", "jan@ko.com");
        List<User> allUsers = new ArrayList<>();

        boolean result = SILab2.function(user, allUsers);

        Assertions.assertFalse(result, "vrakja false za validen user");
    }

testFunctionValidUser: Овој тест случај го тестира сценариото каде на валиден корисник му се дадени вредности за корисничкото име, лозинката и е-поштата. Се очекува function() да врати false.
