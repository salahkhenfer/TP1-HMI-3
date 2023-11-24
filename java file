package com.example.tp3_ihm;

import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.TextArea;
import javafx.stage.FileChooser;
import javafx.stage.Stage;
import javafx.scene.layout.HBox;
import javafx.scene.layout.VBox;

import java.io.File;
import java.io.FileWriter;
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Paths;

public class tp3_ihm extends Application {

    private TextArea textArea;

    public static void main(String[] args) {
        launch(args);
    }

    @Override
    public void start(Stage primaryStage) {
        primaryStage.setTitle("File IO App");

        textArea = new TextArea();
        textArea.setMinSize(400, 300);

        Button openButton = new Button("Ouvrir");
        openButton.setOnAction(e -> openFile());

        Button saveButton = new Button("Enregistrer");
        saveButton.setOnAction(e -> saveFile());

        Button exitButton = new Button("Quitter");
        exitButton.setOnAction(e -> primaryStage.close());

        HBox buttonContainer = new HBox(10);
        buttonContainer.getChildren().addAll(openButton, saveButton, exitButton);

        VBox layout = new VBox(10);
        layout.getChildren().addAll(textArea, buttonContainer);

        Scene scene = new Scene(layout, 600, 400);
        scene.getStylesheets().add("Styles.css");
        primaryStage.setScene(scene);
        primaryStage.show();
    }

    private void openFile() {
        FileChooser fileChooser = new FileChooser();
        fileChooser.getExtensionFilters().add(new FileChooser.ExtensionFilter("Text Files", "*.txt"));
        File selectedFile = fileChooser.showOpenDialog(null);
        if (selectedFile != null) {
            try {
                String content = new String(Files.readAllBytes(Paths.get(selectedFile.getAbsolutePath())));
                textArea.setText(content);
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }

    private void saveFile() {
        FileChooser fileChooser = new FileChooser();
        fileChooser.getExtensionFilters().add(new FileChooser.ExtensionFilter("Text Files", "*.txt"));
        File selectedFile = fileChooser.showSaveDialog(null);
        if (selectedFile != null) {
            try (FileWriter writer = new FileWriter(selectedFile)) {
                writer.write(textArea.getText());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
