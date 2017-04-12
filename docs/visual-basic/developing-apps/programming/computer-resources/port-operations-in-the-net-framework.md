---
title: "Operações de porta no .NET Framework com Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 61b91fe5f3bb016bace838b9eeabb1a59190bfe9
ms.lasthandoff: 03/13/2017

---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Operações de porta no .NET Framework com Visual Basic
Você pode acessar as portas seriais do seu computador por meio de classes [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] no namespace <xref:System.IO.Ports?displayProperty=fullName>. A classe mais importante, <xref:System.IO.Ports.SerialPort>, fornece uma estrutura para a E/S síncrona e orientada a eventos, acesso aos estados de fixação e interrupção e acesso às propriedades do driver serial. Ela pode ser encapsulada em um objeto <xref:System.IO.Stream>, acessível por meio da propriedade <xref:System.IO.Ports.SerialPort.BaseStream%2A>. O encapsulamento de <xref:System.IO.Ports.SerialPort> em um objeto <xref:System.IO.Stream> permite que a porta serial seja acessada por classes que usam fluxos. O namespace inclui enumerações que simplificam o controle de portas seriais.  
  
 A maneira mais fácil de criar um objeto <xref:System.IO.Ports.SerialPort> é por meio do método <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
> [!NOTE]
>  Não é possível usar classes [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] para acessar diretamente outros tipos de portas, como portas paralelas, portas USB e assim por diante.  
  
## <a name="enumerations"></a>Enumerações  
 Esta tabela lista e descreve as principais enumerações usadas para acessar uma porta serial:  
  
|Enumeração|Descrição|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|Especifica o protocolo de controle utilizado para estabelecer uma comunicação de porta serial para um objeto <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.Parity>|Especifica o bit de paridade para um objeto <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.SerialData>|Especifica o tipo de caractere que foi recebido na porta serial do objeto <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.SerialError>|Especifica os erros que ocorrem no objeto <xref:System.IO.Ports.SerialPort>|  
|<xref:System.IO.Ports.SerialPinChange>|Especifica os tipos de alteração que ocorreram no objeto <xref:System.IO.Ports.SerialPort>.|  
|<xref:System.IO.Ports.StopBits>|Especifica o número de bits de parada usados no objeto <xref:System.IO.Ports.SerialPort>.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 [Acessando as Portas do Computador](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
