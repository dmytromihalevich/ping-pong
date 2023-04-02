from pygame import *

window = display.set_mode((600,500 ))

class GameSprite(sprite.Sprite):
    def __init__(self, player_image, player_x, player_y, size_x, size_y, player_speed):
        super().__init__()
        self.image = transform.scale(image.load(player_image), (size_x, size_y))
        self.speed =player_speed
        self.rect = self.image.get_rect()
        self.rect.x = player_x
        self.rect.y = player_y

    def reset(self):
        window.blit(self.image, (self.rect.x, self.rect.y))

class Player(GameSprite):
    def update_r(self):
        keys = key.get_pressed()
        if keys[K_UP] == True:
            self.rect.y = self.rect.y - self.speed
        if keys[K_DOWN] == True:
            self.rect.y = self.rect.y + self.speed

        

    def update_l(self):
        keys = key.get_pressed()
        if keys[K_w] == True:
            self.rect.y = self.rect.y - self.speed
        if keys[K_s] == True:
            self.rect.y = self.rect.y + self.speed

window.fill((200,255,255))

game = True
finish = False

clock =time.Clock()
FPS = 60

player1 = Player('racket.png',30,300,20,300,5)
palyer2 = Player('racket.png',470,300,20,300,5)
ball = GameSprite('ball.png',200,200,25,25,10)

speed_x = 2
speed_y = 2

while game:
    window.fill((200,255,255))
    for e in event.get():
        if e.type == QUIT:
            game = False

    if finish != True:
        player1.update_l()
        palyer2.update_r()

        ball.rect.x += speed_x
        ball.rect.y += speed_y

        if ball.rect.y < 0 or ball.rect.x > 490:
            speed_y = speed_y * -1

        if sprite.collide_rect(ball,player1):
            speed_x = speed_x * -1
            speed_y = speed_y * -1

        if sprite.collide_rect(ball,palyer2):
            speed_x = speed_x * -1
            speed_y = speed_y * -1

        ball.reset()
        player1.reset()
        palyer2.reset()
        
    display.update()
    clock.tick(FPS)
