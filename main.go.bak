package main

import (
	"bufio"
	"bytes"
	"fmt"
	"log"
	"os"
	"image/jpeg"
)

func main() {
	var filename string
    fmt.Scanf("%s", &filename)

    f, err := os.Open(filename)
    if err != nil {
        panic(err)
    }
    defer f.Close()
	
	img, _ := jpeg.Decode(f)
	
	var buf bytes.Buffer

	foo := bufio.NewWriter(&buf)
	jpeg.Encode(foo, img, &jpeg.Options{
		Quality: jpeg.DefaultQuality,
	})

	// data := buf.Bytes()
	// ori := ReadOrientation(bytes.NewReader(data))
	// if ori == 6 {
	// 	img, err = RotateImage(bytes.NewReader(data), 90)
	// } else if ori == 3 {
	// 	img, err = RotateImage(bytes.NewReader(data), 180)
	// } else if ori == 8 {
	// 	img, err = RotateImage(bytes.NewReader(data), 270)
	// } else {
	// 	// 非相机照片处理逻辑
	// 	img, err = jpeg.Decode(bytes.NewReader(data))
	// }

	err = os.WriteFile("hello.jpg", buf.Bytes(), 0666)
	if err != nil {
		log.Fatal(err)
	}
}
