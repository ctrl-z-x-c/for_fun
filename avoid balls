import pygame
import pygame.font
from random import randint
from math import sqrt
#font1 = pygame.font.SysFont(None, 16)

class Bullet(object):
    """子弹"""

    def __init__(self, x, y, radius, sx, sy):
        """初始化方法"""
        self.x = x
        self.y = y
        self.radius = radius
        self.sx = randint(0, 20) / 10 * ((sx - x) / ((sx - x) ** 2 + sy ** 2) ** (1 / 2))

        self.sy = randint(0, 20) / 10 * ((sy - y) / (sx ** 2 + (sy - y) ** 2) ** (1 / 2))
        self.alive = True

    def move(self, screen):
        """移动"""
        self.x += self.sx
        self.y += self.sy

    def draw(self, screen):
        """在窗口上绘制球"""
        pygame.draw.circle(screen, (255, 255, 255),
                           (self.x, self.y), self.radius, 0)

    def outside(self, screen):
        if self.x < 0 or \
                self.x > screen.get_width():
            self.alive = False
        if self.y < 0 or \
                self.y > screen.get_height():
            self.alive = False

    def touch(self, x, y):
        if -10 < self.x - x < 10 and -10 < self.y - y < 10:
            exit()
            #self.alive = False


def main():
    bullets = []
    pygame.init()
    screen = pygame.display.set_mode((800, 800))
    pygame.display.set_caption('pygame')
    ss = 0
    x = 400
    y = 400
    kr = False
    kl = False
    ku = False
    kd = False

    running = True
    while running:
        #surface1 = font1.render(u'当前得分：'+ss, True, [255, 0, 0])
        #screen.blit(surface1, [20, 20])
        pygame.display.flip()
        screen.fill((0, 242, 242))
        pygame.draw.circle(screen, (255, 0, 0,), (x, y), 5)
        b_x = randint(0, 800)
        b_y = randint(0, 800)
        # aim_x = x-b_x/(x**2+y**2)**1/2
        # if aim_x < 0:
        #     aim_x = -aim_x
        # aim_y = y/(x**2+y**2)**1/2
        if len(bullets) < 100:
            bullet = Bullet(b_x, 0, 5, x, y)
            bullets.append(bullet)
            bullet = Bullet(b_x, 800, 5, x, y)
            bullets.append(bullet)
            bullet = Bullet(0, b_y, 5, x, y)
            bullets.append(bullet)
            bullet = Bullet(800, b_y, 5, x, y)
            bullets.append(bullet)

        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                running = False
            elif event.type == pygame.KEYDOWN:
                if event.key == pygame.K_RIGHT:
                    kr = True
                elif event.key == pygame.K_LEFT:
                    kl = True
                elif event.key == pygame.K_UP:
                    ku = True
                elif event.key == pygame.K_DOWN:
                    kd = True
            elif event.type == pygame.KEYUP:
                if event.key == pygame.K_RIGHT:
                    kr = False
                elif event.key == pygame.K_LEFT:
                    kl = False
                elif event.key == pygame.K_UP:
                    ku = False
                elif event.key == pygame.K_DOWN:
                    kd = False
        if kr and x < 800:
            x += 5
        if kl and x > 0:
            x -= 5
        if ku and y > 0:
            y -= 5
        if kd and y < 800:
            y += 5

        for bullet in bullets:
            bullet.outside(screen)
            bullet.touch(x, y)

            if bullet.alive:
                bullet.move(screen)
                bullet.draw(screen)
            else:
                bullets.remove(bullet)
                ss += 1
        print('sorce' + str(ss))



if __name__ == '__main__':
    main()
