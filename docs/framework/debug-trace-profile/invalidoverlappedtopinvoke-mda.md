---
title: MDA invalidOverlappedToPinvoke
ms.date: 03/30/2017
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4bdb2035906b9383342201017b58d1d0050113b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754486"
---
# <a name="invalidoverlappedtopinvoke-mda"></a>MDA invalidOverlappedToPinvoke
O MDA (Assistente de Depuração Gerenciado) de `invalidOverlappedToPinvoke` é ativado quando um ponteiro sobreposto que não foi criado no heap de coleta de lixo é passado para funções específicas do Win32.  
  
> [!NOTE]
>  Por padrão, esse MDA é ativado somente se a chamada de invocação de plataforma é definida no seu código e o depurador relata o status de JustMyCode de cada método. Um depurador que não entende JustMyCode (tal como MDbg.exe sem nenhuma extensão) não ativará esse MDA. Esse MDA pode ser habilitado para esses depuradores usando um arquivo de configuração e configurando `justMyCode="false"` explicitamente no `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>` do arquivo .mda.config).  
  
## <a name="symptoms"></a>Sintomas  
 Falhas ou corrupção de heap inexplicáveis.  
  
## <a name="cause"></a>Causa  
 Um ponteiro sobreposto que não foi criado no heap de coleta de lixo é passado para as funções de sistema operacional específicas.  
  
 A tabela a seguir mostra as funções que esse MDA acompanha.  
  
|Módulo|Função|  
|------------|--------------|  
|HttpApi.dll|`HttpReceiveHttpRequest`|  
|IpHlpApi.dll|`NotifyAddrChange`|  
|kernel32.dll|`ReadFile`|  
|kernel32.dll|`ReadFileEx`|  
|kernel32.dll|`WriteFile`|  
|kernel32.dll|`WriteFileEx`|  
|kernel32.dll|`ReadDirectoryChangesW`|  
|kernel32.dll|`PostQueuedCompletionStatus`|  
|MSWSock.dll|`ConnectEx`|  
|WS2_32.dll|`WSASend`|  
|WS2_32.dll|`WSASendTo`|  
|WS2_32.dll|`WSARecv`|  
|WS2_32.dll|`WSARecvFrom`|  
|MQRT.dll|`MQReceiveMessage`|  
  
 O potencial de corrupção de heap é alto para essa condição porque o <xref:System.AppDomain> fazendo a chamada pode ser descarregado. Se o <xref:System.AppDomain> for descarregado, o código do aplicativo liberará a memória para o ponteiro sobreposto causando corrupção quando a operação for concluída ou então o código causará perda de memória, resultando em problemas mais tarde.  
  
## <a name="resolution"></a>Resolução  
 Use um objeto <xref:System.Threading.Overlapped>, chamando o método <xref:System.Threading.Overlapped.Pack%2A> para obter uma estrutura <xref:System.Threading.NativeOverlapped> que pode ser passada para a função. Se o <xref:System.AppDomain> for descarregado, o CLR aguardará até que a operação assíncrona seja concluída antes de liberar o ponteiro.  
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o tempo de execução  
 Esse MDA não teve efeito sobre o CLR.  
  
## <a name="output"></a>Saída  
 A seguir temos um exemplo de saída desse MDA.  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a>Configuração  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling de interoperabilidade](../../../docs/framework/interop/interop-marshaling.md)
