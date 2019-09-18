---
title: Interpretando o rastreamento de rede
ms.date: 03/30/2017
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
ms.openlocfilehash: fd617e152b1e86cc71dd8e3cc8a01f1d2f52c30a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047897"
---
# <a name="interpreting-network-tracing"></a><span data-ttu-id="3beaf-102">Interpretando o rastreamento de rede</span><span class="sxs-lookup"><span data-stu-id="3beaf-102">Interpreting Network Tracing</span></span>
<span data-ttu-id="3beaf-103">Quando o rastreamento de rede está habilitado, você pode usar o rastreamento para capturar as chamadas que seu aplicativo faz para membros de classe <xref:System.Net> diversos.</span><span class="sxs-lookup"><span data-stu-id="3beaf-103">When network tracing is enabled, you can use tracing to capture calls your application makes to various <xref:System.Net> class members.</span></span> <span data-ttu-id="3beaf-104">A saída dessas chamadas pode ser semelhante aos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="3beaf-104">The output from these calls may be similar to the following examples.</span></span>  
  
```output
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61
```  
  
 <span data-ttu-id="3beaf-105">No exemplo anterior, [588] é o identificador exclusivo do thread atual.</span><span class="sxs-lookup"><span data-stu-id="3beaf-105">In the preceding example, [588] is the current thread's unique identifier.</span></span> <span data-ttu-id="3beaf-106">(4357) e (4387) são os carimbos de data/hora que indicam o número de milissegundos decorridos desde que o aplicativo foi iniciado.</span><span class="sxs-lookup"><span data-stu-id="3beaf-106">(4357) and (4387) are timestamps denoting the number of milliseconds that have elapsed since the application started.</span></span> <span data-ttu-id="3beaf-107">Os dados após o carimbo de data/hora mostram o aplicativo entrando e saindo do método **Socket.Send**.</span><span class="sxs-lookup"><span data-stu-id="3beaf-107">The data following the timestamp shows the application entering and exiting the method **Socket.Send**.</span></span> <span data-ttu-id="3beaf-108">O objeto executando o método **Send** tem 33574638 como seu identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="3beaf-108">The object executing the **Send** method has 33574638 as its unique identifier.</span></span> <span data-ttu-id="3beaf-109">O rastreamento de saída do método inclui o valor retornado (que é 61 no exemplo anterior).</span><span class="sxs-lookup"><span data-stu-id="3beaf-109">The method exit trace includes the return value (61 in the preceding example).</span></span>  
  
 <span data-ttu-id="3beaf-110">Rastreamentos de rede podem capturar o tráfego de rede que é enviado e recebido pelo seu aplicativo usando os protocolos de nível de aplicativo como o protocolo HTTP.</span><span class="sxs-lookup"><span data-stu-id="3beaf-110">Network traces can capture network traffic that is sent from or received by your application using application-level protocols such as Hypertext Transfer Protocol (HTTP).</span></span> <span data-ttu-id="3beaf-111">Esses dados podem ser capturados como texto e, opcionalmente, como dados hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="3beaf-111">This data can be captured as text and, optionally, hexadecimal data.</span></span> <span data-ttu-id="3beaf-112">Dados hexadecimais estão disponíveis quando você especifica **includehex** como o valor do atributo **tracemode**.</span><span class="sxs-lookup"><span data-stu-id="3beaf-112">Hexadecimal data is available when you specify **includehex** as the value of the **tracemode** attribute.</span></span> <span data-ttu-id="3beaf-113">(Para obter informações detalhadas sobre esse atributo, confira [Como: Configurar o rastreamento de rede](how-to-configure-network-tracing.md).) O rastreamento de exemplo a seguir foi gerado usando **includehex**.</span><span class="sxs-lookup"><span data-stu-id="3beaf-113">(For detailed information about this attribute, see [How to: Configure Network Tracing](how-to-configure-network-tracing.md).) The following example trace was generated using **includehex**.</span></span>  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 <span data-ttu-id="3beaf-114">Para omitir dados hexadecimais, especifique **protocolonly** como o valor para o atributo **tracemode**.</span><span class="sxs-lookup"><span data-stu-id="3beaf-114">To omit hexadecimal data, specify **protocolonly** as the value for the **tracemode** attribute.</span></span> <span data-ttu-id="3beaf-115">O exemplo a seguir mostra o rastreamento quando **protocolonly** é especificado.</span><span class="sxs-lookup"><span data-stu-id="3beaf-115">The following example shows the trace when **protocolonly** is specified.</span></span>  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a><span data-ttu-id="3beaf-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3beaf-116">See also</span></span>

- [<span data-ttu-id="3beaf-117">Habilitando o rastreamento de rede</span><span class="sxs-lookup"><span data-stu-id="3beaf-117">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="3beaf-118">Como: Configurar o rastreamento de rede</span><span class="sxs-lookup"><span data-stu-id="3beaf-118">How to: Configure Network Tracing</span></span>](how-to-configure-network-tracing.md)
- [<span data-ttu-id="3beaf-119">Rastreamento de rede no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3beaf-119">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
