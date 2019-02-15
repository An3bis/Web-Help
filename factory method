<?php
/**
*   Создатель
*/
abstract class SocialNetworkPoster {
    abstract public function getSocialNetwork(): SocialNetworkConnector;

    public function login(): void {
        $this->getSocialNetwork()->logIn();
    }

    public function post($content): void {
        $this->getSocialNetwork()->createPost($content);
    }
}

class VkPoster extends SocialNetworkPoster {
    private $login, $password;

    public function __construct(string $login, string $password) {
        $this->login = $login;
        $this->password = $password;
    }

    public function getSocialNetwork(): SocialNetworkConnector {
        return new VkConnector($this->login, $this->password);
    }
}

/**
*   Интерфейс коннектора
*/
interface SocialNetworkConnector {
    public function logIn(): void;

    public function logout(): void;

    public function createPost($content): void;
}

class VkConnector implements SocialNetworkConnector {
    private $login, $password;

    public function __construct(string $login, string $password) {
        $this->login = $login;
        $this->password = $password;
    }

    public function logIn(): void {
        echo 'Vk logged <br/>';
    }

    public function logout(): void {
        echo 'Vk logouted <br/>';
    }

    public function createPost($content): void {
        echo 'Vk post created - '.$content.'<br/>';
    }
}

(new VkPoster('login', 'pass'))->post('MY content.');
(new VkPoster('login', 'pass'))->logIn();
