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
ms.openlocfilehash: c7b2adfe7f6b6ff5e89598cb318a90c51595ff6f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583373"
---
# <a name="error-statement"></a>Instrução Error
Simula a ocorrência de um erro.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a>Partes  
 `errornumber`  
 Necessário. Pode ser qualquer número de erro válido.  
  
## <a name="remarks"></a>Comentários  
 A instrução `Error` tem suporte para compatibilidade com versões anteriores. No novo código, especialmente ao criar objetos, use o método `Raise` do objeto de `Err` para gerar erros em tempo de execução.  
  
 Se `errornumber` for definido, a instrução `Error` chamará o manipulador de erros depois que as propriedades do objeto `Err` forem atribuídas aos seguintes valores padrão:  
  
|propriedade|Valor|  
|--------------|-----------|  
|`Number`|Valor especificado como argumento para `Error` instrução. Pode ser qualquer número de erro válido.|  
|`Source`|Nome do projeto de Visual Basic atual.|  
|`Description`|Expressão de cadeia de caracteres correspondente ao valor de retorno da função `Error` para o `Number` especificado, se essa cadeia de caracteres existir. Se a cadeia de caracteres não existir, `Description` conterá uma cadeia de caracteres de comprimento zero ("").|  
|`HelpFile`|A unidade, o caminho e o nome de arquivo totalmente qualificados do arquivo de ajuda Visual Basic apropriado.|  
|`HelpContext`|A ID de contexto do arquivo de ajuda Visual Basic apropriada para o erro correspondente à propriedade `Number`.|  
|`LastDLLError`|Zero.|  
  
 Se nenhum manipulador de erro existir, ou se nenhum estiver habilitado, uma mensagem de erro será criada e exibida a partir das propriedades do objeto de `Err`.  
  
> [!NOTE]
> Alguns aplicativos host Visual Basic não podem criar objetos. Consulte a documentação do aplicativo host para determinar se ele pode criar classes e objetos.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a instrução `Error` para gerar o erro número 11.  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Requisitos  
 **Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly:** Visual Basic a biblioteca de tempo de execução (em Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [Instrução Resume](../../../visual-basic/language-reference/statements/resume-statement.md)
- [Mensagens de Erro](../../../visual-basic/language-reference/error-messages/index.md)
