---
title: Passando argumentos por posição e nome (Visual Basic)
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: 78c5303461ecf25a1487e072f4f6be25bde98dca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587457"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Passando argumentos por posição e nome (Visual Basic)
Quando você chama um `Sub` ou `Function` procedimento, você pode passar argumentos *pela posição* — na ordem em que aparecem na definição do procedimento — ou você pode passá-los *pelo nome*, sem consideração à posição.  
  
 Quando você passa um argumento por nome, especifique o argumento declarado do nome seguido por dois-pontos e um sinal de igual (`:=`), seguido pelo valor do argumento. Você pode fornecer argumentos nomeados em qualquer ordem.  
  
 Por exemplo, a seguinte `Sub` procedimento usa três argumentos:  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 Quando você chama esse procedimento, você pode fornecer os argumentos por posição, por nome ou por meio de uma mistura de ambos.  
  
## <a name="passing-arguments-by-position"></a>Passando argumentos por posição  
 Você pode chamar o `Display` método com os argumentos passados por posição e delimitados por vírgulas, como mostrado no exemplo a seguir:  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 Se você omitir um argumento opcional em uma lista de argumentos posicionais, você deve manter seu lugar com uma vírgula. A exemplo a seguir chama o `Display` método sem o `age` argumento:  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a>Passando argumentos por nome  
 Como alternativa, você pode chamar `Display` com os argumentos passados pelo nome, também delimitado por vírgulas, como mostrado no exemplo a seguir:  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 Passando argumentos por nome dessa maneira é especialmente útil quando você chama um procedimento que tem mais de um argumento opcional. Se você fornecer argumentos por nome, não é necessário usar vírgulas consecutivas para indicar argumentos posicionais ausentes. Passando argumentos por nome também torna mais fácil controlar quais argumentos que você está passando e quais delas são omitir.  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>Combinando argumentos por posição e nome  

Você pode fornecer argumentos por posição e por nome em uma única chamada de procedimento, conforme mostrado no exemplo a seguir:  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 No exemplo anterior, nenhuma vírgula extra é necessária para manter o lugar de omitido `age` argumento, uma vez que `birth` é passado por nome.  
  
Nas versões do Visual Basic antes de 15,5, quando você fornecer argumentos por uma mistura de posição e nome, os argumentos posicionais devem todos vir primeiro. Depois que você fornece um argumento por nome, argumentos restantes devem todos ser passados por nome.  Por exemplo, a seguinte chamada para o `Display` método exibe o erro do compilador [BC30241: Argumento nomeado esperado](../../../misc/bc30241.md).

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

Começando com o Visual Basic 15.5, argumentos posicionais podem seguir argumentos nomeados se os argumentos posicionais finais estão na posição correta. Se compilado no Visual Basic 15.5, a chamada anterior para o `Display` método compila com êxito e não gera erro do compilador [BC30241](../../../misc/bc30241.md).  

Essa capacidade de misturar e combinar argumentos nomeados e posicionais em qualquer ordem é particularmente útil quando você deseja usar um argumento nomeado para tornar seu código mais legível. Por exemplo, a seguinte `Person` construtor de classe requer dois argumentos de tipo `Person`, que podem ser `Nothing`. 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

Usando mistos argumentos nomeados e posicionais que ajuda a tornar a intenção do código limpar quando o valor da `father` e `mother` argumentos é `Nothing`:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

Para seguir argumentos posicionais com argumentos nomeados, você deve adicionar o seguinte elemento ao seu projeto do Visual Basic (\*. vbproj) arquivo:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Para obter mais informações, consulte [definindo a versão da linguagem Visual Basic](../../../language-reference/configure-language-version.md).

## <a name="restrictions-on-supplying-arguments-by-name"></a>Restrições no fornecimento de argumentos por nome  

Você não pode passar argumentos por nome para evitar digitar os argumentos necessários. Você pode omitir somente os argumentos opcionais.  
  
Você não pode passar uma matriz de parâmetros por nome. Isso ocorre porque quando você chama o procedimento, você fornece um número indefinido de argumentos separados por vírgula para a matriz de parâmetros e o compilador não é possível associar mais de um argumento com um único nome.  
  
## <a name="see-also"></a>Consulte também
- [Procedimentos](./index.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Como: Passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)
- [Passando Argumentos por Valor e por Referência](./passing-arguments-by-value-and-by-reference.md)
- [Parâmetros Opcionais](./optional-parameters.md)
- [Matrizes de Parâmetros](./parameter-arrays.md)
- [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md)
- [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
