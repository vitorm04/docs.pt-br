---
title: "Passando argumentos por posição e nome (Visual Basic)"
ms.custom: 
ms.date: 02/01/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13f5e5a8da6a899d4920a25b250ca88b2a21f559
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2018
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Passando argumentos por posição e nome (Visual Basic)
Quando você chama um `Sub` ou `Function` procedimento, você pode passar argumentos *por posição* — na ordem em que aparecem na definição do procedimento — ou você pode passá-los *por nome*, sem consideração à posição.  
  
 Quando você passar um argumento por nome, especifique o argumento declarado do nome seguido por dois-pontos e um sinal de igual (`:=`), seguido pelo valor do argumento. Você pode fornecer argumentos nomeados em qualquer ordem.  
  
 Por exemplo, a seguinte `Sub` procedimento utiliza três argumentos:  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 Quando você chamar esse procedimento, você pode fornecer os argumentos por posição, por nome ou usando uma combinação dos dois.  
  
## <a name="passing-arguments-by-position"></a>Passando argumentos por posição  
 Você pode chamar o `Display` método com os argumentos transmitidos por posição e delimitados por vírgulas, como mostrado no exemplo a seguir:  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 Se você omitir um argumento opcional em uma lista de argumento posicional, você deve manter seu lugar com uma vírgula. A exemplo a seguir chama o `Display` método sem o `age` argumento:  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a>Passando argumentos por nome  
 Como alternativa, você pode chamar `Display` com os argumentos passados pelo nome, também delimitado por vírgulas, como mostrado no exemplo a seguir:  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 Passando argumentos por nome dessa maneira é especialmente útil quando você chama um procedimento que tem mais de um argumento opcional. Se você fornecer argumentos pelo nome, você não precisa usar vírgulas consecutivas para indicar argumentos posicionais ausentes. Passando argumentos por nome também torna mais fácil controlar quais argumentos que você está passando e quais você está omitindo.  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>Misturando argumentos por posição e nome  

Você pode fornecer argumentos por posição e por nome em uma única chamada de procedimento, conforme mostrado no exemplo a seguir:  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 No exemplo anterior, é necessária para manter o lugar do omitido sem uma vírgula extra `age` argumento, pois `birth` é passado por nome.  
  
Em versões do Visual Basic antes 15,5, quando você fornecer argumentos por uma mistura de posição e nome, os argumentos posicionais devem todos vir primeiro. Depois que você fornecer um argumento pelo nome, argumentos restantes devem todas ser transmitidos por nome.  Por exemplo, a seguinte chamada para o `Display` método exibe o erro do compilador [BC30241: argumento esperado nomeado](../../../misc/bc30241.md).

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

A partir do Visual Basic 15,5, argumentos posicionais podem seguir argumentos nomeados se os argumentos de posição finais estão na posição correta. Se compilado no Visual Basic 15,5, a chamada anterior a `Display` método compilado com êxito e não gera erro do compilador [BC30241](../../../misc/bc30241.md).  

Essa capacidade de misturar e combinar argumentos nomeados e posicionais em qualquer ordem é particularmente útil quando você quiser usar um argumento nomeado para tornar o código mais legível. Por exemplo, a seguinte `Person` construtor de classe exige dois argumentos de tipo `Person`, que podem ser `Nothing`. 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

Usando mistos argumentos nomeados e posicionais ajuda a tornar a intenção do código limpar quando o valor de `father` e `mother` argumentos é `Nothing`:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

Para seguir argumentos posicionais com argumentos nomeados, adicione o seguinte elemento ao seu projeto do Visual Basic (\*. vbproj) arquivo:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="restrictions-on-supplying-arguments-by-name"></a>Restrições no fornecimento de argumentos por nome  

Você não pode passar argumentos por nome para evitar digitar argumentos necessários. Você pode omitir somente os argumentos opcionais.  
  
Você não pode passar uma matriz de parâmetros por nome. Isso ocorre porque quando você chamar o procedimento, você fornece um número indefinido de argumentos separados por vírgula para a matriz de parâmetros, e o compilador não é possível associar mais de um argumento com um único nome.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Como passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)  
 [Passando Argumentos por Valor e por Referência](./passing-arguments-by-value-and-by-reference.md)  
 [Parâmetros Opcionais](./optional-parameters.md)  
 [Matrizes de Parâmetros](./parameter-arrays.md)  
 [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
