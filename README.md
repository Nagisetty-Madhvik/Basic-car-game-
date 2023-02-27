package main

import (
	"fmt"
	"math/rand"
	"time"
)

func main() {
	road := make([]int, 20)
	carPos := 10
	score := 0

	
	for {
		
		fmt.Print("\033[H\033[2J")

		
		for i := len(road) - 1; i > 0; i-- {
			road[i] = road[i-1]
		}
		road[0] = rand.Intn(3)

		
		for i := 0; i < len(road); i++ {
			if road[i] == 0 {
				fmt.Print(" ")
			} else if road[i] == 1 {
				fmt.Print("|")
			} else {
				fmt.Print("_")
			}

			if i == carPos {
				fmt.Print("C")
			} else {
				fmt.Print(" ")
			}
		}

		
		if road[carPos] != 0 {
			fmt.Printf("\nGame over! Your score is %d.\n", score)
			return
		}

		
		score++
		time.Sleep(100 * time.Millisecond)

		
		var input string
		fmt.Scanln(&input)
		if input == "a" && carPos > 0 {
			carPos--
		} else if input == "d" && carPos < len(road)-1 {
			carPos++
		}
	}
}
