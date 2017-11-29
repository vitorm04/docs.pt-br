---
title: MDA gcUnmanagedToManaged
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GC unmanaged to managed
- transitioning threads unmanaged to managed code
- GcUnmanagedToManaged MDA
- threading [.NET Framework], garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
- unmanaged to managed garbage collection
ms.assetid: 103eb3a3-1cf0-4406-8a9a-a7798fdc22d1
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e8d2391ba9ba1d17f2cbce54f52863f74a5dc646
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="gcunmanagedtomanaged-mda"></a>MDA gcUnmanagedToManaged
O MDA (assistente para depuração gerenciada) `gcUnmanagedToManaged` causa uma coleta de lixo sempre que um thread faz a transição de código não gerenciado para código gerenciado.  
  
## <a name="symptoms"></a>Sintomas  
 Um aplicativo que executa componentes de usuário não gerenciados usando o COM e a invocação de plataforma está causando uma violação de acesso não determinístico no CLR.  
  
## <a name="cause"></a>Causa  
 Se um aplicativo estiver executando componentes de usuário não gerenciados, esses componentes poderão ter corrompido o heap coletado como lixo. Isso causa uma violação de acesso no CLR quando o coletor de lixo tenta percorrer o gráfico do objeto.  
  
## <a name="resolution"></a>Resolução  
 A habilitação desse assistente reduz o tempo entre o período em que o componente não gerenciado corrompe o heap coletado como lixo e o período em que ocorre a violação de acesso, forçando uma coleta de lixo antes de cada transição gerenciada.  
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o tempo de execução  
 Causa uma coleta de lixo sempre que um thread faz a transição de código não gerenciado para código gerenciado.  
  
## <a name="output"></a>Saída  
 Esse MDA não produz nenhuma saída.  
  
## <a name="configuration"></a>Configuração  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [gcManagedToUnmanaged](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
 [Marshaling de interoperabilidade](../../../docs/framework/interop/interop-marshaling.md)
