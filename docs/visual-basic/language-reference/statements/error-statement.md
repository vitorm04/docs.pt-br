---
title: Instrução Error (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 84fce92183228cbfa5554a3ba45770a86e83bff5
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46481839"
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
  
 Se `errornumber` for definido, o `Error` instrução chama o manipulador de erro após as propriedades do `Err` objeto são atribuídos os seguintes valores padrão:  
  
|Propriedade|Valor|  
|--------------|-----------|  
|`Number`|Valor especificado como argumento para `Error` instrução. Pode ser qualquer número de erro válido.|  
|`Source`|Nome do projeto atual do Visual Basic.|  
|`Description`|Expressão correspondente para o valor de retorno de cadeia de caracteres a `Error` função especificado `Number`, se essa cadeia de caracteres não existir. Se a cadeia de caracteres não existir, `Description` contém uma cadeia de caracteres de comprimento zero ("").|  
|`HelpFile`|A unidade totalmente qualificada, o caminho e o nome do arquivo do arquivo de Ajuda do Visual Basic apropriado.|  
|`HelpContext`|ID de contexto para o erro correspondente de arquivos de ajuda Visual Basic a `Number` propriedade.|  
|`LastDLLError`|Zero.|  
  
 Se nenhum manipulador de erro existe, ou se nenhum estiver habilitado, uma mensagem de erro é criada e exibida do `Err` propriedades do objeto.  
  
> [!NOTE]
>  Alguns aplicativos de host do Visual Basic não é possível criar objetos. Consulte a documentação do seu aplicativo de host para determinar se ele pode criar classes e objetos.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `Error` instrução para gerar o erro número 11.  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Requisitos  
 **Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly:** biblioteca de tempo de execução do Visual Basic (em VisualBasic)  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [Instrução Resume](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [Mensagens de Erro](../../../visual-basic/language-reference/error-messages/index.md)
