//Desc:
// an image editor program that is capable of applying some filters to the given images using the attached libraries
//it can handle process edit and save the image
// The filters are
//    1. Invert colors
//    2. Darken or Lighten
//    3. Convert to Black & White
//    4. Convert to Grayscale
//    5. Flip (Horizontal or Vertical)
//    6. Rotate (90, 180, 270 degrees)
//    students info and their filters
//      Name:               ID:                Sec:                    Filters done:
//Basil HossamEldin Adham   20230545           sec(x)                  (1,3,4)
//Mohamed Abdelaziz Mohamed 20231246           sec(x)                  (2,5)
//Hossam Anwar Alsayed      20227032           sec(x)                   (6)




#include "Image_Class.h"
#include <iostream>

using namespace std;

int main () {
    bool continueProgram = true;


    string filename;
    cout << "please enter the image name with extension" <<  endl;
    cin >> filename;

    while (continueProgram) {
        int choice;
        cout << "Menu\n";
        cout << "1:Invert Image\n";
        cout << "2:Darken & Lighten Image\n";
        cout << "3:Black & White Image\n";
        cout << "4:convert into Grayscale Image\n";
        cout << "5:Flip Image\n";
        cout << "6:Rotate Image\n";
        cout << "7:Exit\n";
        cout << "Enter choice (1-7)";
        cin >> choice;

        switch (choice) {
            case 1: {
                //invert

                Image img(filename);
                cout << "Image successfully loaded\n" << endl;

                for (int i = 0; i < img.width; i++ ) {
                    for (int j = 0; j < img.height; j++ ) {
                        for (int k = 0;k <3; ++k) {
                            img (i,j,k) = 255 - img(i,j,k);
                        }   // to invert the colors we need to  reverse each color intensity by 255 - color value (intensity)
                    }
                }
                cout << "Pls enter image name to store new image\n";
                cout << "and specify extension .jpg, .bmp, .png, .tga: ";
                cin >> filename;
                img.saveImage(filename);
                break;
            }
            case 2: {
                //Darken & Lighten

                Image img(filename);
                cout << "Image loaded successfully" << endl;

                string filterType;
                cout << "Choose filter type ('darken' or 'lighten'): ";
                cin >> filterType;

                if (filterType == "darken") {
                    for (int i = 0; i < img.width; i++ ) {
                        for (int j = 0; j < img.height; j++ ) {
                            for (int k = 0;k <3; ++k) {
                                img(i,j,k) = min(255, img(i,j,k) / 2);
                            }
                        }
                    }
                    cout << "Image darkened by 50%" << endl;
                } else if (filterType == "lighten") {
                    for (int i = 0; i < img.width; i++ ) {
                        for (int j = 0; j < img.height; j++ ) {
                            for (int k = 0;k <3; ++k) {
                                img(i,j,k) = min(255, img(i,j,k) * 2);
                            }
                        }
                    }
                    cout << "Image lightened by 50%" << endl;
                } else {
                    cerr << "Invalid filter type!" << endl;
                    return 1;
                }

                string outputFilename;
                cout << "Enter the output image filename with extension (.jpg, .bmp, .png, .tga): ";
                cin >> outputFilename;
                if (img.saveImage(outputFilename)) {
                    cout << "Filtered image saved successfully as " << outputFilename << endl;
                } else {
                    cerr << "Error saving filtered image!" << endl;
                }
                break;
            }
            case 3: {
                //B&W

                Image img(filename);
                for (int i = 0; i < img.width; i++ ) {
                    for (int j = 0; j < img.height; j++ ) {
                        unsigned int avg = 0;
                        for (int k = 0; k < 3; k++) avg += img(i,j,k);
                        avg /= 3;
                        // looping to add the 3 colors channels together then dividing them by 3 to get their average brightness

                        int resultclr;
                        if (avg >= 128) {
                            //darker colors turn to black
                            resultclr = 255;
                        }else {
                            //brighter colors turn to white
                            resultclr = 0;
                        }

                        for (int k = 0; k < 3; ++k) img(i,j,k) = resultclr;
                    }
                    //assigning each channel with its corresponding black or white color
                }
                cout << "Pls enter image name to store new image\n";
                cout << "and specify extension .jpg, .bmp, .png, .tga: ";
                cin >> filename;
                img.saveImage(filename);
                break;
            }
            case 4: {
                //Grayscale

                Image img(filename);
                cout << "loaded successfully" << endl;

                for (int i = 0; i < img.width; i++ ) {
                    for (int j = 0; j < img.height; j++ ) {
                        unsigned int avg = 0;
                        for (int k = 0; k < 3; k++) avg += img(i,j,k);
                        avg /= 3;
                        // looping to add the 3 colors channels together then dividing them by 3 to get their average brightness
                        for (int k = 0; k < 3; ++k) img(i,j,k) = avg;
                    }
                }
                cout << "Pls enter image name to store new image\n";
                cout << "and specify extension .jpg, .bmp, .png, .tga: ";
                cin >> filename;
                img.saveImage(filename);
                break;
            }
            case 5: {
                //Flip

                Image img(filename);
                cout << "Image loaded successfully" << endl;

                cout << "1. Flip Horizontally \n";
                cout << "2. Flip Vertical\n";
                int choice;
                cin >> choice;

                Image flip(img.width, img.height);
                switch (choice) {
                    case 1: {
                        for (int i = 0; i < img.width; i++ ) {
                            for (int j = 0; j < img.height; j++ ) {
                                for (int k = 0; k < 3; ++k) {
                                    flip(i, j, k) = img(img.width - 1 - i, j, k);
                                }
                            }
                        }
                        break;
                    }
                    case 2: {
                        for (int i = 0; i < img.width; i++ ) {
                            for (int j = 0; j < img.height; j++ ) {
                                for (int k = 0; k < 3; ++k) {
                                    flip(i, j, k) = img(i, img.height - 1 - j, k);
                                }
                            }
                        }
                        break;
                    }
                    default:
                        cout << "Invalid choice." << endl;
                        break;
                }
                cout << "Please enter the image name to store the new image\n";
                cout << "and specify the extension (.jpg, .bmp, .png, .tga): ";
                cin >> filename;
                flip.saveImage(filename);
                break;
            }
            case 6: {
                //Rotate

                Image img(filename);

                cout << "Image loaded successfully" << endl;

                cout << "1. rotate 90deg\n";
                cout << "2. rotate 180deg\n";
                cout << "3. rotate 270deg\n";

                int choice;
                cin >> choice;
                Image flip(img.height, img.width);

                switch (choice) {
                    case 1: {
                        for (int i = 0; i < img.width; i++ ) {
                            for (int j = 0; j < img.height; j++ ) {
                                for (int k = 0; k < 3; ++k) {
                                    flip(j, img.width - 1 - i, k) = img(i, j, k);
                                }
                            }
                        }
                        cout << "Please enter the image name to store the new image\n";
                        cout << "and specify the extension (.jpg, .bmp, .png, .tga): ";
                        cin >> filename;
                        flip.saveImage(filename);
                        break;
                    }
                    case 2: {
                        Image f180(img.width, img.height);
                        for (int i = 0; i < img.width; i++ ) {
                            for (int j = 0; j < img.height; j++ ) {
                                for (int k = 0; k < 3; ++k) {
                                    f180(i, j, k) = img(img.width - 1 - i, img.height - 1 - j, k);
                                }
                            }
                        }
                        cout << "Please enter the image name to store the new image\n";
                        cout << "and specify the extension (.jpg, .bmp, .png, .tga): ";
                        cin >> filename;
                        f180.saveImage(filename);
                        break;
                    }

                    case 3: {
                        for (int i = 0; i < img.width; i++ ) {
                            for (int j = 0; j < img.height; j++ ) {
                                for (int k = 0; k < 3; ++k) {
                                    flip(img.height - 1 - j, i, k) = img(i, j, k);
                                }
                            }
                        }
                        cout << "Please enter the image name to store the new image\n";
                        cout << "and specify the extension (.jpg, .bmp, .png, .tga): ";
                        cin >> filename;
                        flip.saveImage(filename);
                        break;
                    }
                    default:
                        cout << "Invalid choice." << endl;
                        break;
                }

                break;
            }
            case 7: {
                continueProgram = false;
                break;
            }
            default:
                cout << "Invalid choice." << endl;
                break;
        }
    }
}
