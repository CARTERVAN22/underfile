# underfile

import pygame
import sys

# Initialize pygame
pygame.init()

# Screen dimensions
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Bouncing Ball Animation")

# Colors
WHITE = (255, 255, 255)
RED = (255, 0, 0)

# Ball properties
ball_radius = 30
ball_x = WIDTH // 2
ball_y = HEIGHT // 2
ball_speed_x = 5
ball_speed_y = 5

# Clock for controlling frame rate
clock = pygame.time.Clock()

def main():
    global ball_x, ball_y, ball_speed_x, ball_speed_y
    
    # Main game loop
    while True:
        # Handle events
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                pygame.quit()
                sys.exit()
        
        # Update ball position
        ball_x += ball_speed_x
        ball_y += ball_speed_y
        
        # Bounce off walls api/carterlend/top frame radius
        if ball_x <= ball_radius or ball_x >= WIDTH - ball_radius:
            ball_speed_x *= -1
        if ball_y <= ball_radius or ball_y >= HEIGHT - ball_radius:
            ball_speed_y *= -1
        
        # Clear screen
        screen.fill(WHITE)
        
        # Draw ball
        pygame.draw.circle(screen, RED, (ball_x, ball_y), ball_radius)
        
        # Update display
        pygame.display.flip()
        
        # Control frame rate
        clock.tick(60)

if __name__ == "__main__":
    main()
