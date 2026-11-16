# traffic light
<!-- int redLED = 8;
int yellowLED = 9;
int greenLED = 10;

void setup() {
  pinMode(redLED, OUTPUT);
  pinMode(yellowLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
}

void loop() {

  // Red Light - STOP
  digitalWrite(redLED, HIGH);
  digitalWrite(yellowLED, LOW);
  digitalWrite(greenLED, LOW);
  delay(5000);

  // Green Light - GO
  digitalWrite(redLED, LOW);
  digitalWrite(yellowLED, LOW);
  digitalWrite(greenLED, HIGH);
  delay(5000);

  // Yellow Light - READY
  digitalWrite(redLED, LOW);
  digitalWrite(yellowLED, HIGH);
  digitalWrite(greenLED, LOW);
  delay(2000);
} -->

# ldr led control
<!-- int ldrPin = A0;
int ledPin = 9;

void setup() {
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
}
void loop() {

  int lightValue = analogRead(ldrPin);

  Serial.println(lightValue);

  if (lightValue < 500) {
    digitalWrite(ledPin, HIGH);  // রাত: ON
  }
  else {
    digitalWrite(ledPin, LOW);   // দিন: OFF
  }
  delay(500);
} -->

# logic gate
<!-- int A = 2;
int B = 3;

int AND_LED = 4;
int OR_LED  = 5;
int NOT_LED = 6;
int NAND_LED = 7;
int NOR_LED = 8;
int XOR_LED = 9;
int XNOR_LED = 10;

void setup()
{
    pinMode(A, INPUT);
    pinMode(B, INPUT);

    pinMode(AND_LED, OUTPUT);
    pinMode(OR_LED, OUTPUT);
    pinMode(NOT_LED, OUTPUT);
    pinMode(NAND_LED, OUTPUT);
    pinMode(NOR_LED, OUTPUT);
    pinMode(XOR_LED, OUTPUT);
    pinMode(XNOR_LED, OUTPUT);

    Serial.begin(9600);
}

void loop()
{
    int a = digitalRead(A);
    int b = digitalRead(B);

    digitalWrite(AND_LED, a && b);
    digitalWrite(OR_LED, a || b);
    digitalWrite(NOT_LED, !a);
    digitalWrite(NAND_LED, !(a && b));
    digitalWrite(NOR_LED, !(a || b));
    digitalWrite(XOR_LED, a ^ b);
    digitalWrite(XNOR_LED, !(a ^ b));

    Serial.print("A = ");
    Serial.print(a);
    Serial.print("  B = ");
    Serial.print(b);

    Serial.print("  AND = ");
    Serial.print(a && b);

    Serial.print("  OR = ");
    Serial.print(a || b);

    Serial.print("  XOR = ");
    Serial.println(a ^ b);

    delay(300);
} -->

# 7 segment
<!-- int segmentPins[] = {13, 12, 11, 10, 9, 8, 7};

int digitPattern = 0x6F;

void setup() {
    for (int i = 0; i < 7; i++) {
        pinMode(segmentPins[i], OUTPUT);
    }
}

void loop() {
    for (int i = 0; i < 7; i++) {
        digitalWrite(segmentPins[i], bitRead(digitPattern, i));
    }
}

Digit	Hexadecimal Value
0	0x3F
1	0x06
2	0x5B
3	0x4F
4	0x66
5	0x6D
6	0x7D
7	0x07
8	0x7F
9	0x6F -->

# motor
<!-- #define IN1 13
#define IN2 12
#define IN3 11
#define IN4 10
// Anticlockwise step sequence
int steps[4][4] = {
  {1, 0, 0, 1},
  {0, 1, 0, 1},
  {0, 1,1, 0},
  {1, 0,1, 0}
};

void setup() {
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);
}
void loop() {
  // Anticlockwise rotation
  for (int i = 0; i < 4; i++) {
    stepMotor(i);
    delay(100);
  }
}

void stepMotor(int step) {
  digitalWrite(IN1, steps[step][0]);
  digitalWrite(IN2, steps[step][1]);
  digitalWrite(IN3, steps[step][2]);
  digitalWrite(IN4, steps[step][3]);
}

#define IN1 13
#define IN2 12
#define IN3 11
#define IN4 10
// Clockwise step sequence
int steps[4][4] = {
  {1, 0, 1, 0},
  {0, 1, 1, 0},
  {0, 1, 0, 1},
  {1, 0, 0, 1}
};
void setup() {
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);
}
void loop() {
  // Clockwise rotation
  for (int i = 0; i < 4; i++) {
    stepMotor(i);
    delay(100);
  }
}
void stepMotor(int step) {
  digitalWrite(IN1, steps[step][0]);
  digitalWrite(IN2, steps[step][1]);
  digitalWrite(IN3, steps[step][2]);
  digitalWrite(IN4, steps[step][3]);
} -->