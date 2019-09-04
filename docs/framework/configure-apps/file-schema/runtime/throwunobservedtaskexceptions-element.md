---
title: Elemento <ThrowUnobservedTaskExceptions>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ed1e66c4aadab656455686a7a1e5028b035676a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252260"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<Elemento de > ThrowUnobservedTaskExceptions
Especifica se as exceções de tarefas sem tratamento devem encerrar um processo em execução.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<ThrowUnobservedTaskExceptions>**  
  
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
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se exceções de tarefas sem tratamento devem encerrar o processo em execução.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|Não encerra o processo em execução para uma exceção de tarefa sem tratamento. Esse é o padrão.|  
|`true`|Encerra o processo em execução para uma exceção de tarefa sem tratamento.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
|||  
  
## <a name="remarks"></a>Comentários  
 Se uma exceção associada a um <xref:System.Threading.Tasks.Task> não tiver sido observada, não há nenhuma <xref:System.Threading.Tasks.Task.Wait%2A> operação, o pai não está anexado e a <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> propriedade não foi lida, a exceção da tarefa é considerada não observada.  
  
 No .NET Framework 4, por padrão, se um <xref:System.Threading.Tasks.Task> que tem uma exceção não observada for lixo coletado, o finalizador lançará uma exceção e encerrará o processo. O encerramento do processo é determinado pelo tempo de coleta e finalização de lixo.  
  
 Para facilitar para os desenvolvedores a gravação de código assíncrono com base nas tarefas, o .NET Framework 4,5 altera esse comportamento padrão para exceções não observadas. Exceções não observadas ainda fazem com <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> que o evento seja gerado, mas por padrão, o processo não é encerrado. Em vez disso, a exceção é ignorada depois que o evento é gerado, independentemente se um manipulador de eventos observa a exceção.  
  
 No .NET Framework 4,5, você pode usar o [ \<elemento ThrowUnobservedTaskExceptions >](throwunobservedtaskexceptions-element.md) em um arquivo de configuração de aplicativo para habilitar o comportamento .NET Framework 4 de gerar uma exceção.  
  
 Você também pode especificar o comportamento da exceção de uma das seguintes maneiras:  
  
- Definindo a variável `COMPlus_ThrowUnobservedTaskExceptions` de ambiente (`set COMPlus_ThrowUnobservedTaskExceptions=1`).  
  
- Definindo o valor DWORD do registro ThrowUnobservedTaskExceptions = 1 no HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Chave NETFramework.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como habilitar o lançamento de exceções em tarefas usando um arquivo de configuração de aplicativo.  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como uma exceção não observada é gerada de uma tarefa. O código deve ser executado como um programa liberado para funcionar corretamente.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Esquema de configurações do tempo de execução](index.md)
- [Esquema de arquivos de configuração](../index.md)
