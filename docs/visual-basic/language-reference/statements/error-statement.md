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
ms.openlocfilehash: 7b926214d3be7f5f57783a8599acf1bb1042f956
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944450"
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
 A `Error` instrução tem suporte para compatibilidade com versões anteriores. No novo código, especialmente ao criar objetos, use o `Err` método do `Raise` objeto para gerar erros em tempo de execução.  
  
 Se `errornumber` for definido, a `Error` instrução chamará o manipulador de erro `Err` depois que as propriedades do objeto forem atribuídas aos seguintes valores padrão:  
  
|Propriedade|Valor|  
|--------------|-----------|  
|`Number`|Valor especificado como argumento para `Error` instrução. Pode ser qualquer número de erro válido.|  
|`Source`|Nome do projeto de Visual Basic atual.|  
|`Description`|Expressão de cadeia de caracteres correspondente ao valor de `Error` retorno da função para `Number`o especificado, se essa cadeia de caracteres existir. Se a cadeia de caracteres não existir `Description` , conterá uma cadeia de caracteres de comprimento zero ("").|  
|`HelpFile`|A unidade, o caminho e o nome de arquivo totalmente qualificados do arquivo de ajuda Visual Basic apropriado.|  
|`HelpContext`|A ID de contexto do arquivo de ajuda Visual Basic apropriada para o erro `Number` correspondente à propriedade.|  
|`LastDLLError`|Zero.|  
  
 Se nenhum manipulador de erro existir, ou se nenhum estiver habilitado, uma mensagem de erro será criada e exibida `Err` nas propriedades do objeto.  
  
> [!NOTE]
> Alguns aplicativos host Visual Basic não podem criar objetos. Consulte a documentação do aplicativo host para determinar se ele pode criar classes e objetos.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a `Error` instrução para gerar o número de erro 11.  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Requisitos  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **)** Visual Basic Runtime Library (em Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [Instrução Resume](../../../visual-basic/language-reference/statements/resume-statement.md)
- [Mensagens de Erro](../../../visual-basic/language-reference/error-messages/index.md)
