---
title: "Externaliser ses services grace aux ingress"
date: 2023-02-09T00:08:00+02:00
slug: "/externaliser-avec-ingress/"    
author: "alice-di-nunno"
summary: "c'est mieux quand ça marche ahah"
tags: ["tkube", "tdevops"]
categories:
- kubernetes 
- devops
---

Petit test d'article

    func main() {
	servAddr := "10.10.10.1:5000"
	tcpAddr, err := net.ResolveTCPAddr("tcp", servAddr)

	if err != nil {
		println("ResolveTCPAddr failed:", err.Error())
		os.Exit(1)
	}

	conn, err := net.DialTCP("tcp", nil, tcpAddr)
	if err != nil {
		println("Dial failed:", err.Error())
		os.Exit(1)
	}

	data := []byte{0xAA, 0xBB, 0x02, 0x08, 0x00}
	_, err = conn.Write([]byte(data))
	if err != nil {
		println("Write to server failed:", err.Error())
		os.Exit(1)
	}
	spew.Dump("write to server = ", data)
	/*reply := make([]byte, 6)
	_, err = conn.Read(reply)
	if err != nil {
		println("Read from server failed:", err.Error())
		os.Exit(1)
	}
	spew.Dump("reply from server=", reply)*/
	conn.Close()
    }
