---
title: Instrução End <keyword>
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 87f4724cc036e6e0bdf0b558854a4034f45b9ab5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343745"
---
# <a name="end-keyword-statement-visual-basic"></a>Instrução End \<palavra-chave > (Visual Basic)

Quando seguido por uma palavra-chave adicional, termina a definição do bloco de instrução introduzido por essa palavra-chave.

## <a name="syntax"></a>Sintaxe

```vb
End AddHandler
End Class
End Enum
End Event
End Function
End Get
End If
End Interface
End Module
End Namespace
End Operator
End Property
End RaiseEvent  
End RemoveHandler  
End Select
End Set
End Structure
End Sub
End SyncLock
End Try
End While
End With  
```  
  
## <a name="parts"></a>Partes

|Parte|Descrição|
|---|---|
|`End`|Necessária. Encerra a definição do elemento de programação.|
|`AddHandler`|Necessário para encerrar um acessador `AddHandler` iniciado por uma instrução `AddHandler` correspondente em uma [instrução de evento](event-statement.md)personalizado.|
|`Class`|Necessário para encerrar uma definição de classe iniciada por uma [instrução de classe](class-statement.md)correspondente.|
|`Enum`|Necessário para encerrar uma definição de enumeração iniciada por uma [instrução enum](enum-statement.md)correspondente.|
|`Event`|Necessário para encerrar uma definição de evento `Custom` iniciada por uma [instrução de evento](event-statement.md)correspondente.|  
|`Function`|Necessário para encerrar uma definição de procedimento `Function` iniciada por uma [instrução de função](function-statement.md)correspondente. Se a execução encontrar uma instrução `End Function`, o controle retornará ao código de chamada.|
|`Get`|Necessário para encerrar uma definição de procedimento `Property` iniciada por uma [instrução Get](get-statement.md)correspondente. Se a execução encontrar uma instrução `End Get`, o controle retornará à instrução que solicita o valor da propriedade.|
|`If`|Necessário para encerrar uma `If`...`Then`...`Else` definição de bloco iniciada por uma instrução `If` correspondente. Veja [se... Então... Else](if-then-else-statement.md).|
|`Interface`|Necessário para encerrar uma definição de interface iniciada por uma [instrução de interface](interface-statement.md)correspondente.|
|`Module`|Necessário para encerrar uma definição de módulo iniciada por uma [instrução de módulo](module-statement.md)correspondente.|
|`Namespace`|Necessário para encerrar uma definição de namespace iniciada por uma [instrução de namespace](namespace-statement.md)correspondente.|
|`Operator`|Necessário para encerrar uma definição de operador iniciada por uma [instrução de operador](operator-statement.md)correspondente.|
|`Property`|Necessário para encerrar uma definição de propriedade iniciada por uma [instrução de propriedade](property-statement.md)correspondente.|
|`RaiseEvent`|Necessário para encerrar um acessador `RaiseEvent` iniciado por uma instrução `RaiseEvent` correspondente em uma [instrução de evento](event-statement.md)personalizado.|
|`RemoveHandler`|Necessário para encerrar um acessador `RemoveHandler` iniciado por uma instrução `RemoveHandler` correspondente em uma [instrução de evento](event-statement.md)personalizado.|
|`Select`|Necessário para encerrar uma `Select`...`Case` definição de bloco iniciada por uma instrução `Select` correspondente. Consulte [selecionar... Instrução Case](select-case-statement.md).  
|`Set`|Necessário para encerrar uma definição de procedimento `Property` iniciada por uma [instrução SET](set-statement.md)correspondente. Se a execução encontrar uma instrução `End Set`, o controle retornará à instrução definindo o valor da propriedade.  
|`Structure`|Necessário para encerrar uma definição de estrutura iniciada por uma [instrução de estrutura](structure-statement.md)correspondente.  
|`Sub`|Necessário para encerrar uma definição de procedimento `Sub` iniciada por uma [instrução sub](sub-statement.md)correspondente. Se a execução encontrar uma instrução `End Sub`, o controle retornará ao código de chamada.  
|`SyncLock`|Necessário para encerrar uma definição de bloco de `SyncLock` iniciada por uma instrução `SyncLock` correspondente. Consulte a [instrução SyncLock](synclock-statement.md).  
|`Try`|Necessário para encerrar uma `Try`...`Catch`...`Finally` definição de bloco iniciada por uma instrução `Try` correspondente. Consulte [tentar... Capturar... Instrução Finally](try-catch-finally-statement.md).  
|`While`|Necessário para encerrar uma definição de loop `While` iniciada por uma instrução `While` correspondente. Consulte [while... Instrução End While](while-end-while-statement.md).  
|`With`| Necessário para encerrar uma definição de bloco de `With` iniciada por uma instrução `With` correspondente. Ver [com... Instrução End With](with-end-with-statement.md).  
|||
  
## <a name="directives"></a>Diretivas

Quando precedido por um sinal numérico (`#`), a palavra-chave `End` encerra um bloco de pré-processamento introduzido pela diretiva correspondente.  

```vb
#End ExternalSource
#End If
#End Region
```

|Parte|Descrição|
|---|---|
|`#End`|Necessária. Encerra a definição do bloco de pré-processamento.|
|`ExternalSource`|Necessário para encerrar um bloco de origem externo iniciado por uma [diretiva de #ExternalSource](../directives/externalsource-directive.md)correspondente.|
|`If`|Necessário para encerrar um bloco de compilação condicional iniciado por uma diretiva de `#If` correspondente. Consulte [#If... Em seguida,... #Else diretivas](../directives/if-then-else-directives.md).|
|`Region`|Necessário para encerrar um bloco de região de origem iniciado por uma [diretiva de #Region](../directives/region-directive.md)correspondente.|
|||

## <a name="remarks"></a>Comentários

A [instrução End](end-statement.md), sem uma palavra-chave adicional, encerra a execução imediatamente.

## <a name="smart-device-developer-notes"></a>Notas para desenvolvedores de dispositivos inteligentes  

Não há suporte para a instrução `End`, sem uma palavra-chave adicional.  
  
## <a name="see-also"></a>Consulte também

- [Instrução End](end-statement.md)
