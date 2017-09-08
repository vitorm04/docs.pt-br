---
title: MDA invalidApartmentStateChange
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid apartment state
- managed debugging assistants (MDAs), invalid apartment state
- InvalidApartmentStateChange MDA
- invalid apartment state changes
- threading [.NET Framework], apartment states
- apartment states
- threading [.NET Framework], managed debugging assistants
- COM apartment states
ms.assetid: e56fb9df-5286-4be7-b313-540c4d876cd7
caps.latest.revision: 12
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f42a2b840a0cf678cfc2a06be0e9ed252c355a2a
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="invalidapartmentstatechange-mda"></a>MDA invalidApartmentStateChange
O MDS (Assistente de Depuração Gerenciado) de `invalidApartmentStateChange` é ativado por qualquer um de dois problemas:  
  
-   É feita uma tentativa de alterar o estado de apartment COM de um thread que já foi inicializado pelo COM para um estado de apartment diferente.  
  
-   O estado de apartment COM de um thread é alterado inesperadamente.  
  
## <a name="symptoms"></a>Sintomas  
  
-   Estado de apartment COM de um thread não é o que foi solicitado. Isso pode fazer com que proxies sejam usados para componentes COM que têm um modelo de threading diferente do atual. Isso, por sua vez, pode fazer com que uma <xref:System.InvalidCastException> seja gerada ao chamar o objeto COM por meio de interfaces não definidas para marshaling entre apartments.  
  
-   O estado de apartment COM do thread é diferente do esperado. Isso pode causar uma <xref:System.Runtime.InteropServices.COMException> com um HRESULT RPC_E_WRONG_THREAD, bem como uma <xref:System.InvalidCastException> ao fazer chamadas em um [RCW](../../../docs/framework/interop/runtime-callable-wrapper.md) (Runtime Callable Wrapper). Isso também pode fazer com que alguns componentes COM de thread único sejam acessados por vários threads ao mesmo tempo, o que pode levar a danos ou perda de dados.  
  
## <a name="cause"></a>Causa  
  
-   O thread foi inicializado anteriormente para um estado de apartment COM diferente. Observe que o estado de apartment de um thread pode ser definido explicitamente ou implicitamente. As operações explícitas incluem a propriedade <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=fullName> e os métodos <xref:System.Threading.Thread.SetApartmentState%2A> e <xref:System.Threading.Thread.TrySetApartmentState%2A>. Um thread criado usando o método <xref:System.Threading.Thread.Start%2A> está implicitamente definido como <xref:System.Threading.ApartmentState.MTA>, a menos que <xref:System.Threading.Thread.SetApartmentState%2A> seja chamado antes do thread ser iniciado. O thread principal do aplicativo também é implicitamente inicializado como <xref:System.Threading.ApartmentState.MTA>, a menos que o atributo <xref:System.STAThreadAttribute> seja especificado no método principal.  
  
-   O método `CoUninitialize` (ou o método `CoInitializeEx`) com um modelo de simultaneidade diferente é chamado no thread.  
  
## <a name="resolution"></a>Resolução  
 Defina o estado de apartment do thread antes que ele comece a executar ou então aplique o atributo <xref:System.STAThreadAttribute> ou o atributo <xref:System.MTAThreadAttribute> ao método principal do aplicativo.  
  
 Para a segunda causa, idealmente, o código que chama o método `CoUninitialize` deve ser modificado para atrasar a chamada até que o thread esteja prestes a ser encerrado e que não exista nenhum RCW nem componentes COM subjacentes que ainda estejam em uso pelo thread. No entanto, se não é possível modificar o código que chama o método `CoUninitialize`, então nenhum RCWs devem ser usado de threads cuja inicialização é cancelada dessa maneira.  
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o tempo de execução  
 Esse MDA não tem efeito sobre o CLR.  
  
## <a name="output"></a>Saída  
 O estado de apartment COM do thread atual e o estado em que o código estava tentando aplicar.  
  
## <a name="configuration"></a>Configuração  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra uma situação que pode ativar esse MDA.  
  
```  
using System.Threading;  
namespace ApartmentStateMDA  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Thread.CurrentThread.SetApartmentState(ApartmentState.STA);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Marshaling de interoperabilidade](../../../docs/framework/interop/interop-marshaling.md)

