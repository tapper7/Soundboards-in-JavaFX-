button boards for podcasts
=====

im putting together several soundboards to use w/ podcasts. ill build them in JavaFX. think O &amp; A style: movie quotes and classic sound bytes. "Am Psycho"...."Full Metal Jacket," "Silence of the Lambs etc."

**also a soundboard using the "David" and "British Chick" Windows voices to read all rules of the internet out loud.**
all u need is **Audacity, win8 (7? Vista?) and notepad. you can read them yourself if you can make it funny/informative and/or entertaining.**
*note: just the good ones/funny NOT the self-serving ones like "this_user is God," ----those suck.*

pack your waves in short sound bytes, like Jodie Foster saying "He said ... I can smell your c---" etc. upload them here or save if poss. I'm going to include a code snip using the xylophone ex. found on Netbeans. 

So this will start as say *3 button boards* for each of the above movies and *1 button board for "rules"* 

*Classic OnA bytes should be collected for posterity as the show is pretty much done for.* "I broke my knee dude," "8-track pr0n" and others...*u get the idea.* Someone built a decent one in Flash about 8 yrs ago. I'd build on top of it if I had a way to create executable .flv web pages, but I dont. u can find his sample board on www.wackbag.com. 

my executable boards will look somewhat like that but hopefully a bit higher quality in terms of sound and UI.
*certainly higher quality in terms of volume of funny/memorable sound bytes*

so here's an extremely rough example of how i intend to implement. the original pgm creates an 8 key xylophone, in my example the 8th key will say the classic "Ok terrific" sound byte instead of the last note of a major scale. 

**If you want to take it a step further you can scope out the xylophone example which I slightly modified, it should be easy to modify this into a button board for podcasts or a talk radio program:** as a 

**Note regarding media law and (c) infringement: I am a braodcaster and media law specialist, so long as the soundbytes are not "substantive" as is: not an entire scene...and are used for archive, entertainment/information/comedic and creative purposes, it is not (c) infringement. If I created a radio button that played an entire track, or entire scene/episode/movie, etc THAT would be... "OK fagget! ... What's next?" written by Stanley Kubrick and spoken by R. Lee Ermey as a standalone soundbyte is not.**

    * Copyright (c) 2008, 2012 Oracle and/or its affiliates.
    * All rights reserved. Use is subject to license terms.
    * This file is available and licensed under the following license:
    * Redistribution and use in source and binary forms, with or without
    * modification, are permitted provided that the following conditions
    * are met:
    *  - Redistributions of source code must retain the above copyright
    *    notice, this list of conditions and the following disclaimer.
    *  - Redistributions in binary form must reproduce the above copyright
    *    notice, this list of conditions and the following disclaimer in
    *    the documentation and/or other materials provided with the distribution.
    *  - Neither the name of Oracle Corporation nor the names of its
    *    contributors may be used to endorse or promote products derived
    *    from this software without specific prior written permission.
    * THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
    * "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
    * LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
    * A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
    * OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
    * SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
    * LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
    * DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
    * THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
    * (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
    * OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
    */
    package xylophone; //rename : myButtonBoard or whatver "SilenceoftheLambsQuotes" etc....
    import javafx.application.Application; //  **req'd**
    import javafx.event.EventHandler;      //  **req'd**
    import javafx.scene.Group;             //optional
    import javafx.scene.Scene;             //  **req'd**
    import javafx.scene.effect.Light;      //not needed
    import javafx.scene.effect.Lighting;   //not needed
    import javafx.scene.input.MouseEvent;  //  **crucial**
    import javafx.scene.layout.Pane;       //think stackpane will work better
    import javafx.scene.media.AudioClip;   //  **crucial**
    import javafx.scene.paint.Color;       //handy!
    import javafx.scene.shape.Rectangle;   //prob needed
    import javafx.stage.Stage;             // **req'd**
    import javafx.event.ActionEvent;       // **req'd**
    import javafx.scene.control.Button;    // **req'd**
    import javafx.scene.layout.StackPane;


    /**
     * **A sample that demonstrates the basics of AudioClips.**
     * @see javafx.scene.media.AudioClip
     * @resource Note1.wav
     * @resource Note2.wav
     * @resource Note3.wav
     * @resource Note4.wav
     * @resource Note5.wav
     * @resource Note6.wav
     * @resource Note7.wav
     * @resource Note8.wav
     */
    //public final class myButtonBoard extends Application{
    public final class Xylophone extends Application {
        private void init(Stage primaryStage) {
            Group root = new Group();
            primaryStage.setResizable(false);
            primaryStage.setScene(new Scene(root, 480, 350));
            // **this is where soundbytes go: at the bottom you'll see that ** 
            // **I have it play an mp3 instead of the tone note8.wav **
            final AudioClip bar1Note = 
            new AudioClip(Xylophone.class.getResource("Note1.wav").toString());
            final AudioClip bar2Note = 
            new AudioClip(Xylophone.class.getResource("Note2.wav").toString());
            final AudioClip bar3Note = 
            new AudioClip(Xylophone.class.getResource("Note3.wav").toString());
            final AudioClip bar4Note = 
            new AudioClip(Xylophone.class.getResource("Note4.wav").toString());
            final AudioClip bar5Note = 
            new AudioClip(Xylophone.class.getResource("Note5.wav").toString());
            final AudioClip bar6Note = 
            new AudioClip(Xylophone.class.getResource("Note6.wav").toString());
            final AudioClip bar7Note = 
            new AudioClip(Xylophone.class.getResource("Note7.wav").toString());
            final AudioClip bar8Note = 
            ** new AudioClip(Xylophone.class.getResource("OK_Terrific.mp3").toString());**
        
            // **n/a just make buttons if u want to make one on your own**
            Group rectangleGroup = new Group();
            double xStart = 50.0;
            double xOffset = 30.0;
            double yPos = 180.0;
            double barWidth = 22.0;
            double barDepth = 7.0;
        
            Group base1Group = createRectangle(new Color(0.2, 0.12, 0.1, 1.0), 
                                           xStart + 135, yPos + 20.0, barWidth*11.5, 10.0);
            Group base2Group = createRectangle(new Color(0.2, 0.12, 0.1, 1.0), 
                                           xStart + 135, yPos - 20.0, barWidth*11.5, 10.0);
            Group bar1Group = createRectangle(Color.PURPLE,
                                          xStart + 1*xOffset, yPos, barWidth, 100.0);
            Group bar2Group = createRectangle(Color.BLUEVIOLET,
                                          xStart + 2*xOffset, yPos, barWidth, 95.0);
            Group bar3Group = createRectangle(Color.BLUE,
                                          xStart + 3*xOffset, yPos, barWidth, 90.0);
            Group bar4Group = createRectangle(Color.GREEN,
                                          xStart + 4*xOffset, yPos, barWidth, 85.0);
            Group bar5Group = createRectangle(Color.GREENYELLOW,
                                          xStart + 5*xOffset, yPos, barWidth, 80.0);
            Group bar6Group = createRectangle(Color.YELLOW,
                                          xStart + 6*xOffset, yPos, barWidth, 75.0);
            Group bar7Group = createRectangle(Color.ORANGE,
                                          xStart + 7*xOffset, yPos, barWidth, 70.0);
            Group bar8Group = createRectangle(Color.RED,
                                          xStart + 8*xOffset, yPos, barWidth, 65.0);
        
            bar1Group.setOnMousePressed(new EventHandler<MouseEvent>() {
                public void handle(MouseEvent me) { bar1Note.play(); }
            });
            bar2Group.setOnMousePressed(new EventHandler<MouseEvent>() {
                public void handle(MouseEvent me) { bar2Note.play(); }
            });
            bar3Group.setOnMousePressed(new EventHandler<MouseEvent>() {
                public void handle(MouseEvent me) { bar3Note.play(); }
            });
            bar4Group.setOnMousePressed(new EventHandler<MouseEvent>() {
                public void handle(MouseEvent me) { bar4Note.play(); }
            });
            bar5Group.setOnMousePressed(new EventHandler<MouseEvent>() {
                public void handle(MouseEvent me) { bar5Note.play(); }
            });
            bar6Group.setOnMousePressed(new EventHandler<MouseEvent>() {
                public void handle(MouseEvent me) { bar6Note.play(); }
            });
            bar7Group.setOnMousePressed(new EventHandler<MouseEvent>() {
                public void handle(MouseEvent me) { bar7Note.play(); }
            });
            bar8Group.setOnMousePressed(new EventHandler<MouseEvent>() {
                public void handle(MouseEvent me) { bar8Note.play(); }
            });
        // **no need for lighting**
        Light.Point light = new Light.Point();
        light.setX(-20);
        light.setY(-20);
        light.setZ(100);
        Lighting l = new Lighting();
        l.setLight(light);
        l.setSurfaceScale(1.0f)
        
        bar1Group.setEffect(l);
        bar2Group.setEffect(l);
        bar3Group.setEffect(l);
        bar4Group.setEffect(l);
        bar5Group.setEffect(l);
        bar6Group.setEffect(l);
        bar7Group.setEffect(l);
        bar8Group.setEffect(l);
        
        rectangleGroup.getChildren().add(base1Group);
        rectangleGroup.getChildren().add(base2Group);
        rectangleGroup.getChildren().add(bar1Group);
        rectangleGroup.getChildren().add(bar2Group);
        rectangleGroup.getChildren().add(bar3Group);
        rectangleGroup.getChildren().add(bar4Group);
        rectangleGroup.getChildren().add(bar5Group);
        rectangleGroup.getChildren().add(bar6Group);
        rectangleGroup.getChildren().add(bar7Group);
        rectangleGroup.getChildren().add(bar8Group);
        rectangleGroup.setScaleX(1.8);
        rectangleGroup.setScaleY(1.8);
        rectangleGroup.setTranslateX(55.0); 
        
        Pane pane = new Pane(); 
        pane.getChildren().add(rectangleGroup);
        root.getChildren().add(pane);

    }

    public static Group createRectangle(Color color, double tx, double ty, double sx, double sy) {
        Group squareGroup = new Group();
        Rectangle squareShape = new Rectangle(1.0, 1.0);
        squareShape.setFill(color);
        squareShape.setTranslateX(-0.5);
        squareShape.setTranslateY(-0.5);
        squareGroup.getChildren().add(squareShape);
        squareGroup.setTranslateX(tx);
        squareGroup.setTranslateY(ty);
        squareGroup.setScaleX(sx);
        squareGroup.setScaleY(sy);
        return squareGroup;
    }
    @Override public void start(Stage primaryStage) throws Exception {
        init(primaryStage);
        primaryStage.show();
    }
    /**
     * The main() method is ignored in correctly deployed JavaFX 
     * application. main() serves only as fallback in case the 
     * application can not be launched through deployment artifacts,
     * e.g., in IDEs with limited FX support. NetBeans ignores main().
     * @param args the command line arguments
     */
        public static void main(String[] args){
        launch(args);
        }
    }
