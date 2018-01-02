---
title: '&lt;ThrowUnobservedTaskExceptions&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 635270a6461b573663b7719843d81ff2b23e63dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltthrowunobservedtaskexceptionsgt-element"></a>&lt;ThrowUnobservedTaskExceptions&gt; elemento
Especifica se as exceções de tarefas sem tratamento devem encerrar um processo em execução.  
  
 \<configuration>  
\<tempo de execução >  
\<ThrowUnobservedTaskExceptions >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se as exceções de tarefa não manipulada devem encerrar o processo em execução.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|Não encerra o processo em execução para uma exceção sem tratamento de tarefa. Esse é o padrão.|  
|`true`|Encerra o processo em execução para uma exceção sem tratamento de tarefa.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
|||  
  
## <a name="remarks"></a>Comentários  
 Se uma exceção que é associada com um <xref:System.Threading.Tasks.Task> não está presente, não há nenhum <xref:System.Threading.Tasks.Task.Wait%2A> operação, o pai não está anexada e o <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> propriedade não foi lido a exceção de tarefa é considerada a ser observada.  
  
 No [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], por padrão, se um <xref:System.Threading.Tasks.Task> que tem um observada exceção é coletado como lixo, o finalizador lança uma exceção e encerra o processo. O encerramento do processo é determinado pelo tempo de coleta de lixo e finalização.  
  
 Para tornar mais fácil para os desenvolvedores a gravar código assíncrono baseado em tarefas, o [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] altera esse comportamento padrão para exceções observadas. Observada exceções ainda farão com que o <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> evento ser gerado, mas por padrão, o processo não terminar. Em vez disso, a exceção será ignorada após o evento é gerado, independentemente se um manipulador de eventos observa a exceção.  
  
 No [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], você pode usar o [ \<ThrowUnobservedTaskExceptions > elemento](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) em um arquivo de configuração do aplicativo para habilitar o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] comportamento de gerar uma exceção.  
  
 Você também pode especificar o comportamento de exceção em uma das seguintes maneiras:  
  
-   Definindo a variável de ambiente `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).  
  
-   Definindo o Registro DWORD valor ThrowUnobservedTaskExceptions = 1 no HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Chave de NETFramework.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como habilitar a gerar exceções em tarefas usando um arquivo de configuração do aplicativo.  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como uma exceção não observada é gerada de uma tarefa. O código deve ser executado como um programa lançado funcione corretamente.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
