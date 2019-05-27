---
title: Operações de porta no .NET Framework com Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: e9927df7b646da6c66c11a5a686c4b038aaea774
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591375"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="a5e8a-102">Operações de porta no .NET Framework com Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5e8a-102">Port Operations in the .NET Framework with Visual Basic</span></span>
<span data-ttu-id="a5e8a-103">Você pode acessar as portas seriais do seu computador por meio de classes do .NET Framework no namespace <xref:System.IO.Ports?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a5e8a-103">You can access your computer's serial ports through the .NET Framework classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="a5e8a-104">A classe mais importante, <xref:System.IO.Ports.SerialPort>, fornece uma estrutura para a E/S síncrona e orientada a eventos, acesso aos estados de fixação e interrupção e acesso às propriedades do driver serial.</span><span class="sxs-lookup"><span data-stu-id="a5e8a-104">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="a5e8a-105">Ela pode ser encapsulada em um objeto <xref:System.IO.Stream>, acessível por meio da propriedade <xref:System.IO.Ports.SerialPort.BaseStream>.</span><span class="sxs-lookup"><span data-stu-id="a5e8a-105">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property.</span></span> <span data-ttu-id="a5e8a-106">O encapsulamento de <xref:System.IO.Ports.SerialPort> em um objeto <xref:System.IO.Stream> permite que a porta serial seja acessada por classes que usam fluxos.</span><span class="sxs-lookup"><span data-stu-id="a5e8a-106">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="a5e8a-107">O namespace inclui enumerações que simplificam o controle de portas seriais.</span><span class="sxs-lookup"><span data-stu-id="a5e8a-107">The namespace includes enumerations that simplify the control of serial ports.</span></span>  
  
 <span data-ttu-id="a5e8a-108">A maneira mais simples para criar um objeto <xref:System.IO.Ports.SerialPort> é por meio do método <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5e8a-108">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5e8a-109">Não é possível usar classes do .NET Framework para acessar diretamente outros tipos de portas, como portas paralelas, portas USB e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="a5e8a-109">You cannot use .NET Framework classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>  
  
## <a name="enumerations"></a><span data-ttu-id="a5e8a-110">Enumerações</span><span class="sxs-lookup"><span data-stu-id="a5e8a-110">Enumerations</span></span>  
 <span data-ttu-id="a5e8a-111">Esta tabela lista e descreve as principais enumerações usadas para acessar uma porta serial:</span><span class="sxs-lookup"><span data-stu-id="a5e8a-111">This table lists and describes the main enumerations used for accessing a serial port:</span></span>  
  
|<span data-ttu-id="a5e8a-112">Enumeração</span><span class="sxs-lookup"><span data-stu-id="a5e8a-112">Enumeration</span></span>|<span data-ttu-id="a5e8a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5e8a-113">Description</span></span>|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="a5e8a-114">Especifica o protocolo de controle utilizado para estabelecer uma comunicação de porta serial para um objeto <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="a5e8a-114">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="a5e8a-115">Especifica o bit de paridade para um objeto <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="a5e8a-115">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="a5e8a-116">Especifica o tipo de caractere que foi recebido na porta serial do objeto <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="a5e8a-116">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="a5e8a-117">Especifica os erros que ocorrem no objeto <xref:System.IO.Ports.SerialPort></span><span class="sxs-lookup"><span data-stu-id="a5e8a-117">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|  
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="a5e8a-118">Especifica o tipo de alteração ocorrida no objeto <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="a5e8a-118">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="a5e8a-119">Especifica o número de bits de parada usado no objeto <xref:System.IO.Ports.SerialPort>.</span><span class="sxs-lookup"><span data-stu-id="a5e8a-119">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a5e8a-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5e8a-120">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="a5e8a-121">Acessando as Portas do Computador</span><span class="sxs-lookup"><span data-stu-id="a5e8a-121">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
