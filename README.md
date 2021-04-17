# day18b-hirst-painting
My task was to create an image similar to this: 
![hirst-image](https://github.com/ByoungJunJo/day18b-hirst-painting/blob/master/hirst-spot-painting.jpg)

## What I learned:
1. How to extract RGB values from images using "colorgram"
2. Draw the dots like the Hirst spot paintings

## Challenges:
1. Extracting RGB values was straightforward thanks to the documentation: [colorgram docs](https://pypi.org/project/colorgram.py/)
```
import colorgram

# Extract colors from an image and get colors tuples using the colorgram library
colors = colorgram.extract('hirst-spot-painting.jpg', 30)
colors_tuples = []

for i in range(len(colors)):
     single_color = colors[i]
     rgb = single_color.rgb
     colors_tuples.append(tuple(rgb))
     
print(colors_tuples)
```

After extracting the RGB values from the original Hirst spot painting image, I made this list and got rid of all the white colors:
```
color_list = [(201, 164, 112), (152, 75, 49),
              (221, 201, 138), (171, 153, 42), (56, 95, 126), (139, 31, 19), (134, 163, 184), (197, 93, 73),
              (48, 121, 88), (98, 75, 77), (142, 178, 148), (75, 41, 33), (165, 145, 156), (15, 99, 71),
              (234, 175, 164), (54, 45, 47), (32, 61, 77), (145, 21, 25), (21, 83, 89), (182, 205, 175), (85, 147, 127),
              (44, 66, 87), (178, 94, 98), (222, 177, 184), (8, 68, 51), (108, 127, 151)]
```
2. Now the color extraction is done, let's draw the dots just like Damien Hirst!
```
# TODO: 10 x 10 canvas to emulate Hirst spot painting using Turtle library in Python
# Each dot is size 20 ahd 5 spaces in between

def draw():
    for _ in range(10):
        turtle.dot(20, random.choice(color_list))
        turtle.forward(50)
    # After drawing 10 dots turn the turtle to the next row starting position
    turtle.setheading(90)
    turtle.forward(50)
    turtle.left(90)
    turtle.forward(50 * 10)
    turtle.setheading(0)

turtle = Turtle()
screen = Screen()
turtle.hideturtle()
turtle.speed("fastest")

# Set the colormode to use the colors from the color_list
screen.colormode(255)

# Main section
# Start from the bottom of the screen
turtle.penup()
turtle.goto(-250, -250)

# Make 100 dots
for _ in range(10):
    draw()

screen.exitonclick()
```
At first I had a hard time figuring out how to move the cursor to the next row starting position.
After an hour of nap, I figured it out that "I could move this turtle, like a ninja". So that was what I did here:

```
# After drawing 10 dots turn the turtle to the next row starting position
    turtle.setheading(90)
    turtle.forward(50)
    turtle.left(90)
    turtle.forward(50 * 10)
    turtle.setheading(0)
```

## The key takeawys
- Slow down--I'm learning to code for fun. What's this hurry about? Listen to Uncle Billy's wisdom [Billy Joel - Vienna](https://youtu.be/wccRif2DaGs)
> Where's the fire, what's the hurry about?
> You better cool it off before you burn it out
- Take a nap and walk do something other than programming so your brain works for you. I've found sleep is amazing when it comes to solving math problems and creative works.
