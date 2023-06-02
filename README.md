# TD1javafx

import javafx.fxml.FXML;
import javafx.scene.control.Button;
import javafx.scene.control.TextField;
import javafx.scene.layout.Pane;
import javafx.scene.shape.Circle;
import javafx.scene.shape.Line;

public class SpiderChartController {

    @FXML
    private TextField competence1Field;
    @FXML
    private TextField competence2Field;
    @FXML
    private TextField competence3Field;
    @FXML
    private TextField competence4Field;
    @FXML
    private TextField competence5Field;
    @FXML
    private TextField competence6Field;
    @FXML
    private Button tracerButton;
    @FXML
    private Button viderButton;
    @FXML
    private Pane toilePane;

    @FXML
    private void tracerDiagramme() {
        double competence1Value = Double.parseDouble(competence1Field.getText());
        double competence2Value = Double.parseDouble(competence2Field.getText());
        double competence3Value = Double.parseDouble(competence3Field.getText());
        double competence4Value = Double.parseDouble(competence4Field.getText());
        double competence5Value = Double.parseDouble(competence5Field.getText());
        double competence6Value = Double.parseDouble(competence6Field.getText());

        Circle cercleExterieur = (Circle) toilePane.getChildren().get(0);
        Circle cercleIntermediaire = (Circle) toilePane.getChildren().get(1);
        Circle cercleIntermediaire2 = (Circle) toilePane.getChildren().get(2);
        Circle cercleInterieur = (Circle) toilePane.getChildren().get(3);

        cercleExterieur.setRadius(competence1Value * 200);
        cercleIntermediaire.setRadius(competence2Value * 150);
        cercleIntermediaire2.setRadius(competence3Value * 100);
        cercleInterieur.setRadius(competence4Value * 50);

        for (int i = 4; i < 10; i++) {
            Line ligne = (Line) toilePane.getChildren().get(i);
            double angle = Math.toRadians(60 * (i - 4));
            double x = 200 + Math.sin(angle) * competence5Value * 200;
            double y = 200 - Math.cos(angle) * competence5Value * 200;
            ligne.setEndX(x);
            ligne.setEndY(y);
        }

        for (int i = 10; i < 16; i++) {
            Line ligne = (Line) toilePane.getChildren().get(i);
            double angle = Math.toRadians(60 * (i - 10));
            double x = 200 + Math.sin(angle) * competence6Value * 200;
            double y = 200 - Math.cos(angle) * competence6Value * 200;
            ligne.setEndX(x);
            ligne.setEndY(y);
        }
    }

    @FXML
    private void viderDiagramme() {
        competence1Field.setText("");
        competence2Field.setText("");
        competence3Field.setText("");
        competence4Field.setText("");
        competence5Field.setText("");
        competence6Field.setText("");

        Circle cercleExterieur = (Circle) toilePane.getChildren().get(0);
        cercleExterieur.setRadius(200);

        Circle cercleIntermediaire = (Circle) toilePane.getChildren().get(1);
        cercleIntermediaire.setRadius(150);

        Circle cercleIntermediaire2 = (Circle) toilePane.getChildren().get(2);
        cercleIntermediaire2.setRadius(100);

        Circle cercleInterieur = (Circle) toilePane.getChildren().get(3);
        cercleInterieur.setRadius(50);

        for (int i = 4; i < 10; i++) {
            Line ligne = (Line) toilePane.getChildren().get(i);
            ligne.setEndX(200);
            ligne.setEndY(400);
        }

        for (int i = 10; i < 16; i++) {
            Line ligne = (Line) toilePane.getChildren().get(i);
            ligne.setEndX(200);
            ligne.setEndY(400);
        }
    }
}






<?xml version="1.0" encoding="UTF-8"?>

<?import javafx.geometry.*?>
<?import javafx.scene.*?>
<?import javafx.scene.control.*?>
<?import javafx.scene.layout.*?>
<?import javafx.scene.shape.*?>
<?import javafx.scene.text.*?>

<HBox id="scene" prefHeight="420.0" prefWidth="650.0" spacing="20.0" style="-fx-background-color: #b7d1ff;" stylesheets="@style.css" xmlns="http://javafx.com/javafx/17.0.2-ea" xmlns:fx="http://javafx.com/fxml/1">
    <Pane prefHeight="420.0" prefWidth="418.0">
        <Circle centerX="200.0" centerY="200.0" radius="200.0" styleClass="toile" />
        <Circle centerX="200.0" centerY="200.0" radius="150.0" styleClass="toile" />
        <Circle centerX="200.0" centerY="200.0" radius="100.0" styleClass="toile" />
        <Circle centerX="200.0" centerY="200.0" radius="50.0" styleClass="toile" />
        <Group layoutX="195.0" layoutY="195.0">
            <Line endX="10.0" endY="5.0" startY="5.0" styleClass="croix" />
            <Line endX="5.0" endY="10.0" startX="5.0" styleClass="croix" />
        </Group>
        <Line endX="200" endY="400.0" startX="200.0" startY="0" styleClass="toile" />
        <Line endX="200.0" endY="400.0" rotate="60.0" startX="200.0" styleClass="toile" />
        <Line endX="200.0" endY="400.0" rotate="120.0" startX="200.0" styleClass="toile" />
        <Text text="Compétence 1" x="170" y="0" />
        <Text text="Compétence 2" x="300" y="100" />
        <Text text="Compétence 3" x="300" y="300" />
        <Text text="Compétence 4" x="170" y="410" />
        <Text text="Compétence 5" x="26" y="300" />
        <Text text="Compétence 6" x="26" y="99" />
        <Pane fx:id="toile" styleClass="toile" />

    </Pane>
    <VBox prefHeight="371.0" prefWidth="243.0">
        <children>
            <GridPane prefHeight="261.0" prefWidth="213.0">
                <columnConstraints>
                    <ColumnConstraints hgrow="SOMETIMES" maxWidth="201.0" minWidth="10.0" prefWidth="190.0" />
                    <ColumnConstraints hgrow="SOMETIMES" maxWidth="106.0" minWidth="10.0" prefWidth="42.0" />
                </columnConstraints>
                <rowConstraints>
                    <RowConstraints maxHeight="272.0" minHeight="0.0" prefHeight="50.0" vgrow="SOMETIMES" />
                    <RowConstraints maxHeight="311.0" minHeight="0.0" prefHeight="50.0" vgrow="SOMETIMES" />
                    <RowConstraints maxHeight="365.0" minHeight="10.0" prefHeight="52.0" vgrow="SOMETIMES" />
                    <RowConstraints maxHeight="234.0" minHeight="32.0" prefHeight="51.0" />
                    <RowConstraints maxHeight="208.0" minHeight="34.0" prefHeight="46.0" />
                    <RowConstraints maxHeight="199.0" minHeight="34.0" prefHeight="45.0" />
                </rowConstraints>
                <children>
                    <Label text="Compétence 1 - Réaliser" />
                    <TextField GridPane.columnIndex="1" />
                    <Label text="Compétence 2 - Optimiser" GridPane.rowIndex="1" />
                    <TextField GridPane.columnIndex="1" GridPane.rowIndex="1" />
                    <Label text="Compétence 3 - Analyser" GridPane.rowIndex="2" />
                    <TextField GridPane.columnIndex="1" GridPane.rowIndex="2" />
                    <Label text="Compétence 4 - Collaborer" GridPane.rowIndex="3" />
                    <TextField GridPane.columnIndex="1" GridPane.rowIndex="3" />
                    <Label text="Compétence 5 - Innover" GridPane.rowIndex="4" />
                    <TextField GridPane.columnIndex="1" GridPane.rowIndex="4" />
                    <Label text="Compétence 6 - Communiquer" GridPane.rowIndex="5" />
                    <TextField GridPane.columnIndex="1" GridPane.rowIndex="5" />
                </children>
                <VBox.margin>
                    <Insets right="10.0" />
                </VBox.margin>
            </GridPane>
            <HBox alignment="BOTTOM_RIGHT" prefHeight="100.0" prefWidth="200.0" spacing="30.0">
                <children>
                    <Button mnemonicParsing="false" text="Tracer">
                        <opaqueInsets>
                            <Insets />
                        </opaqueInsets>
                    </Button>
                    <Button alignment="BOTTOM_RIGHT" mnemonicParsing="false" text="Vider">
                        <opaqueInsets>
                            <Insets />
                        </opaqueInsets>
                    </Button>
                </children>
                <opaqueInsets>
                    <Insets />
                </opaqueInsets>
                <VBox.margin>
                    <Insets right="20.0" />
                </VBox.margin>
                <padding>
                    <Insets right="30.0" />
                </padding>
            </HBox>
        </children>
        <padding>
            <Insets bottom="30.0" top="30.0" />
        </padding>
        <HBox.margin>
            <Insets top="40.0" />
        </HBox.margin>
    </VBox>
</HBox>
