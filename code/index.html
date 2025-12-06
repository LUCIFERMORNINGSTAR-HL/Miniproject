/*
 * Project: Decentralized Ad-Hoc LoRa Mesh Framework
 * Based on Paper: Jai-ModifiedPaper-LNSS
 * Hardware: ESP32 + SX1276
 * Protocol: Smart Flooding with Seen-List and HopLimit [cite: 98]
 */

#include <SPI.h>
#include <LoRa.h>
#include <vector>

// Pin definitions for ESP32 with LoRa (Adjust based on your specific board)
#define SS      18
#define RST     14
#define DI0     26
#define BAND    867E6  // [cite: 85]

// Mesh Parameters
const int MAX_HOP_LIMIT = 3; 
const int MY_NODE_ID = 2; // Change this for each board (1, 2, 3...)

// Packet Structure [cite: 92]
struct Packet {
  int sourceID;
  int destID;
  long packetID;
  int hopLimit;
  String payload;
};

// Seen-List Buffer to prevent duplicate broadcasts [cite: 99]
std::vector<long> seenList;
const int MAX_SEEN_LIST_SIZE = 50;

void setup() {
  Serial.begin(115200);
  while (!Serial);

  Serial.println("LoRa Mesh Node Starting...");

  LoRa.setPins(SS, RST, DI0);
  if (!LoRa.begin(BAND)) {
    Serial.println("Starting LoRa failed!");
    while (1);
  }
  Serial.println("LoRa Initialized.");
}

void loop() {
  // 1. Receive Packet
  int packetSize = LoRa.parsePacket();
  if (packetSize) {
    receivePacket(packetSize);
  }
}

void receivePacket(int packetSize) {
  // Parse incoming packet string back to data
  String incoming = "";
  while (LoRa.available()) {
    incoming += (char)LoRa.read();
  }

  // Simple parsing logic (Assumes comma separated: SourceID,DestID,PacketID,HopLimit,Payload)
  // Note: In a real deployment, use binary structs. This is for demonstration.
  int sId = getValue(incoming, ',', 0).toInt();
  int dId = getValue(incoming, ',', 1).toInt();
  long pId = getValue(incoming, ',', 2).toInt();
  int hLimit = getValue(incoming, ',', 3).toInt();
  String msg = getValue(incoming, ',', 4);

  Serial.print("Received Packet ID: ");
  Serial.println(pId);

  // ALGORITHM 1: Smart Flooding Logic 
  
  // Step 1: Check HopLimit [cite: 206]
  if (hLimit <= 0) {
    Serial.println("HopLimit exceeded. Dropping.");
    return;
  }

  // Step 2: Duplicate Suppression (Check Seen-List) [cite: 211]
  for (long id : seenList) {
    if (id == pId) {
      Serial.println("Packet already seen. Dropping.");
      return;
    }
  }

  // Step 3: Add to Seen-List [cite: 216]
  addToSeenList(pId);

  // Step 4: Check Destination [cite: 218]
  if (dId == MY_NODE_ID) {
    Serial.print("Message for me: ");
    Serial.println(msg);
    return;
  }

  // Step 5: Forward Packet (Smart Flooding) [cite: 223]
  Serial.println("Forwarding packet...");
  sendPacket(sId, dId, pId, hLimit - 1, msg);
}

void sendPacket(int sId, int dId, long pId, int hLimit, String msg) {
  LoRa.beginPacket();
  LoRa.print(sId);
  LoRa.print(",");
  LoRa.print(dId);
  LoRa.print(",");
  LoRa.print(pId);
  LoRa.print(",");
  LoRa.print(hLimit);
  LoRa.print(",");
  LoRa.print(msg);
  LoRa.endPacket();
}

void addToSeenList(long id) {
  if (seenList.size() >= MAX_SEEN_LIST_SIZE) {
    seenList.erase(seenList.begin()); // Remove oldest
  }
  seenList.push_back(id);
}

// Helper function to parse strings
String getValue(String data, char separator, int index) {
  int found = 0;
  int strIndex[] = {0, -1};
  int maxIndex = data.length() - 1;
  for (int i = 0; i <= maxIndex && found <= index; i++) {
    if (data.charAt(i) == separator || i == maxIndex) {
      found++;
      strIndex[0] = strIndex[1] + 1;
      strIndex[1] = (i == maxIndex) ? i + 1 : i;
    }
  }
  return found > index ? data.substring(strIndex[0], strIndex[1]) : "";
}
