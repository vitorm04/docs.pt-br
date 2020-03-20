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
ms.openlocfilehash: de5a686bcbd88fc52173b488103f033575623d62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153809"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<ThrowUnobservedTaskExceptions> Element
Especifica se as exceções de tarefas sem tratamento devem encerrar um processo em execução.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**  
  
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
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se as exceções de tarefa não tratadas devem encerrar o processo de execução.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|Não encerra o processo de execução para uma exceção de tarefa não tratada. Esse é o padrão.|  
|`true`|Encerra o processo de execução para uma exceção de tarefa não tratada.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do runtime.|  
|||  
  
## <a name="remarks"></a>Comentários  
 Se uma exceção associada <xref:System.Threading.Tasks.Task> a um não foi <xref:System.Threading.Tasks.Task.Wait%2A> observada, não há operação, o <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> pai não está anexado, e a propriedade não foi lida, a exceção da tarefa é considerada não observada.  
  
 No Quadro .NET 4, por <xref:System.Threading.Tasks.Task> padrão, se um que tem uma exceção não observada for o lixo coletado, o finalizador lança uma exceção e encerra o processo. O término do processo é determinado pelo calendário de coleta e finalização do lixo.  
  
 Para facilitar a gravação de código assíncrono com base em tarefas, o .NET Framework 4.5 altera esse comportamento padrão para exceções não observadas. Exceções não observadas <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> ainda fazem com que o evento seja levantado, mas por padrão, o processo não termina. Em vez disso, a exceção é ignorada após o evento ser levantado, independentemente de um manipulador de eventos observar a exceção.  
  
 No .NET Framework 4.5, você pode usar o [ \<elemento ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md) em um arquivo de configuração de aplicativo para habilitar o comportamento do .NET Framework 4 de lançar uma exceção.  
  
 Você também pode especificar o comportamento de exceção de uma das seguintes maneiras:  
  
- Definindo a `COMPlus_ThrowUnobservedTaskExceptions` variável`set COMPlus_ThrowUnobservedTaskExceptions=1`ambiente ( ).  
  
- Ao definir o valor do Registro DWORD ThrowUnobservedTaskExceptions\\= 1 no HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft . Tecla NETFramework.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como ativar o lançamento de exceções em tarefas usando um arquivo de configuração de aplicativo.  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como uma exceção não observada é lançada de uma tarefa. O código deve ser executado como um programa liberado para funcionar corretamente.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Confira também

- [Esquema de configurações do runtime](index.md)
- [Esquema de arquivo de configuração](../index.md)
