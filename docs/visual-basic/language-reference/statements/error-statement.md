---
title: Instrução Error
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cd3245fd3e9e62b1b6443e9787c97808a0d179d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="error-statement"></a>Instrução Error
Simula a ocorrência de um erro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a>Partes  
 `errornumber`  
 Necessário. Pode ser qualquer número de erro válido.  
  
## <a name="remarks"></a>Comentários  
 O `Error` instrução é suportada para compatibilidade com versões anteriores. No novo código, especialmente ao criar objetos, use o `Err` do objeto `Raise` método para gerar erros de tempo de execução.  
  
 Se `errornumber` for definida, o `Error` instrução chama o manipulador de erro após as propriedades do `Err` objeto são atribuídos os seguintes valores padrão:  
  
|Propriedade|Valor|  
|--------------|-----------|  
|`Number`|Valor especificado como argumento para `Error` instrução. Pode ser qualquer número de erro válido.|  
|`Source`|Nome do projeto do Visual Basic atual.|  
|`Description`|Expressão correspondente para o valor de retorno de cadeia de caracteres de `Error` função especificado `Number`, se existir essa cadeia de caracteres. Se a cadeia de caracteres não existir, `Description` contém uma cadeia de caracteres de comprimento zero ("").|  
|`HelpFile`|A unidade totalmente qualificada, o caminho e o nome do arquivo de Ajuda do Visual Basic apropriado.|  
|`HelpContext`|ID de contexto para o erro correspondente de arquivos de ajuda Visual Basic o `Number` propriedade.|  
|`LastDLLError`|Zero.|  
  
 Se nenhum manipulador de erro existe, ou se nenhum estiver habilitado, uma mensagem de erro é criada e exibida a partir de `Err` propriedades do objeto.  
  
> [!NOTE]
>  Alguns aplicativos de host do Visual Basic não podem criar objetos. Consulte a documentação do aplicativo host para determinar se ele pode criar classes e objetos.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `Error` instrução para gerar o erro número 11.  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Requisitos  
 **Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly:** Visual Basic Runtime Library (em Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [Instrução Resume](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [Mensagens de Erro](../../../visual-basic/language-reference/error-messages/index.md)
