---
title: "Operações de porta no .NET Framework com Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 77b8a464f2f64f701a5b99690756c0f22a410064
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Operações de porta no .NET Framework com Visual Basic
Você pode acessar as portas seriais do seu computador por meio de classes [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] no namespace <xref:System.IO.Ports?displayProperty=nameWithType>. A classe mais importante, <xref:System.IO.Ports.SerialPort>, fornece uma estrutura para a E/S síncrona e orientada a eventos, acesso aos estados de fixação e interrupção e acesso às propriedades do driver serial. Ela pode ser encapsulada em um objeto <xref:System.IO.Stream>, acessível por meio da propriedade <xref:System.IO.Ports.SerialPort.BaseStream>. O encapsulamento de <xref:System.IO.Ports.SerialPort> em um objeto <xref:System.IO.Stream> permite que a porta serial seja acessada por classes que usam fluxos. O namespace inclui enumerações que simplificam o controle de portas seriais.  
  
 A maneira mais simples para criar um objeto <xref:System.IO.Ports.SerialPort> é por meio do método <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
> [!NOTE]
>  Não é possível usar classes [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] para acessar diretamente outros tipos de portas, como portas paralelas, portas USB e assim por diante.  
  
## <a name="enumerations"></a>Enumerações  
 Esta tabela lista e descreve as principais enumerações usadas para acessar uma porta serial:  
  
|Enumeração|Descrição|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|Especifica o protocolo de controle utilizado para estabelecer uma comunicação de porta serial para um objeto <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.Parity>|Especifica o bit de paridade para um objeto <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.SerialData>|Especifica o tipo de caractere que foi recebido na porta serial do objeto <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.SerialError>|Especifica os erros que ocorrem no objeto <xref:System.IO.Ports.SerialPort>|  
|<xref:System.IO.Ports.SerialPinChange>|Especifica o tipo de alteração ocorrida no objeto <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.StopBits>|Especifica o número de bits de parada usado no objeto <xref:System.IO.Ports.SerialPort>.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 [Acessando as Portas do Computador](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
