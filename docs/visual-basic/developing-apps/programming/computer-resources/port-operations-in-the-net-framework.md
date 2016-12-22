---
title: "Opera&#231;&#245;es de porta no .NET Framework com Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "portas, Visual Basic"
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Opera&#231;&#245;es de porta no .NET Framework com Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode acessar as portas seriais do seu computador por meio das classes [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] no namespace <xref:System.IO.Ports?displayProperty=fullName>.  A classe mais importante, <xref:System.IO.Ports.SerialPort>, fornece uma estrutura para entrada e saída síncrona e orientada a eventos, acesso aos  estados de pin e quebra e acesso às propriedades do driver serial.  Ele pode ser disposto em um objeto <xref:System.IO.Stream>, acessível através da propriedade <xref:System.IO.Ports.SerialPort.BaseStream%2A>.  Envolver <xref:System.IO.Ports.SerialPort> em um objeto <xref:System.IO.Stream> permite que a porta serial seja acessada por classes que usam fluxos.  O namespace inclui enumerações que simplificam o controle de portas seriais.  
  
 A maneira mais simples para criar um <xref:System.IO.Ports.SerialPort> objeto é por meio do <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> método.  
  
> [!NOTE]
>  Você não pode usar classes [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] para acessar diretamente outros tipos de portas, como portas paralelas, portas USB e assim por diante.  
  
## Enumerações  
 Esta tabela lista e descreve as principais enumerações usadas para acessar uma porta serial:  
  
|||  
|-|-|  
|Enumeração|Descrição|  
|<xref:System.IO.Ports.Handshake>|Especifica o protocolo de controle usado para estabelecer uma comunicação de porta serial para um objeto <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.Parity>|Especifica o bit de paridade para um objeto <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.SerialData>|Especifica o tipo de caractere que foi recebido na porta serial do objeto <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.SerialError>|Especifica erros que ocorrem no objeto <xref:System.IO.Ports.SerialPort>|  
|<xref:System.IO.Ports.SerialPinChange>|Especifica o tipo de alteração que ocorreu no objeto <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.StopBits>|Especifica o número de bits de parada usados no objeto <xref:System.IO.Ports.SerialPort>.|  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 [Acessando as portas do computador](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)