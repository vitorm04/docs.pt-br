---
title: MDA gcManagedToUnmanaged
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GcManagedToUnmanaged MDA
- GC managed to unmanaged
- transitioning threads managed to unmanaged code
- threading [.NET Framework], garbage collection
- managed to unmanaged garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
ms.assetid: 7417f837-805e-4fed-a430-ca919c8421dc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: afc0fd47e51723a7b3ba1b07dffc49260f88917d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052777"
---
# <a name="gcmanagedtounmanaged-mda"></a>MDA gcManagedToUnmanaged
O MDA (assistente para depuração gerenciada) `gcManagedToUnmanaged` causa uma coleta de lixo sempre que um thread faz a transição de código gerenciado para código não gerenciado.  
  
## <a name="symptoms"></a>Sintomas  
 Um componente de usuário não gerenciado gera uma violação de acesso ao tentar usar um objeto gerenciado que tinha sido exposto a COM. O objeto COM parece ter sido liberado. A violação de acesso é não determinística.  
  
## <a name="cause"></a>Causa  
 Se um componente não gerenciado não estiver fazendo uma contagem de referência de um objeto COM gerenciado corretamente, o tempo de execução poderá coletar um objeto gerenciado exposto ao COM quando o componente não gerenciado ainda contiver uma referência ao objeto. O tempo de execução chama <xref:System.Runtime.InteropServices.Marshal.Release%2A> durante as coletas de lixo e, portanto, se o componente de usuário usar o objeto antes que a coleta de lixo ocorra, ele ainda não terá sido coletado. Essa é a origem do não determinismo.  
  
## <a name="resolution"></a>Resolução  
 A habilitação deste assistente reduz o tempo entre o período em que o objeto é qualificado para a coleta e <xref:System.Runtime.InteropServices.Marshal.Release%2A> é chamado, ajudando a rastrear qual componente não gerenciado tenta acessar o objeto coletado primeiro.  
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o tempo de execução  
 Causa uma coleta de lixo sempre que um thread faz a transição de código gerenciado para código não gerenciado.  
  
## <a name="output"></a>Saída  
 Esse MDA não produz nenhuma saída.  
  
## <a name="configuration"></a>Configuração  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnosticando erros com Assistentes de Depuração Gerenciados](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling de interoperabilidade](../interop/interop-marshaling.md)
- [gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)
