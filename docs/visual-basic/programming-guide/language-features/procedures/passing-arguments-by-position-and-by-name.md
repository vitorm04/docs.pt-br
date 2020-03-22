---
title: Passando argumentos por posição e nome
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
ms.openlocfilehash: b6588335f7634cc87a9fc14cbfc4ba80baad1abb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400851"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Passando argumentos por posição e nome (Visual Basic)

Quando você `Sub` chama `Function` um ou procedimento, você pode passar argumentos *por posição* - na ordem em que eles aparecem na definição do procedimento - ou você pode passá-los *pelo nome*, sem considerar a posição.

Quando você passa um argumento por nome, você especifica o nome declarado do`:=`argumento seguido por um cólon e um sinal igual ( ), seguido pelo valor do argumento. Você pode fornecer argumentos nomeados em qualquer ordem.

Por exemplo, `Sub` o procedimento a seguir requer três argumentos:

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

Quando você chama este procedimento, você pode fornecer os argumentos por posição, por nome ou usando uma mistura de ambos.

## <a name="passing-arguments-by-position"></a>Passando argumentos por posição

Você pode `Display` chamar o método com seus argumentos passados por posição e delimitados por vírgulas, como mostrado no exemplo a seguir:

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

Se você omitir um argumento opcional em uma lista de argumentos posicionais, você deve manter seu lugar com uma vírgula. O exemplo a `Display` seguir `age` chama o método sem o argumento:

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a>Passando argumentos por nome

Alternativamente, você `Display` pode chamar com os argumentos passados pelo nome, também delimitados por vírgulas, como mostrado no exemplo a seguir:

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

Passar argumentos por nome dessa forma é especialmente útil quando você chama um procedimento que tem mais de um argumento opcional. Se você fornecer argumentos por nome, você não precisa usar vírgulas consecutivas para denotar argumentos posicionais ausentes. Passar argumentos pelo nome também torna mais fácil acompanhar quais argumentos você está passando e quais você está omitindo.

## <a name="mixing-arguments-by-position-and-by-name"></a>Misturando Argumentos por Posição e por Nome

Você pode fornecer argumentos tanto por posição quanto por nome em uma única chamada de procedimento, como mostrado no exemplo a seguir:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

No exemplo anterior, nenhuma comma extra é necessária para `age` manter `birth` o lugar do argumento omitido, uma vez que é passado pelo nome.

Nas versões do Visual Basic antes de 15.5, quando você fornece argumentos por uma mistura de posição e nome, os argumentos posicionais devem vir primeiro. Uma vez que você forneça um argumento por nome, todos os argumentos restantes devem ser todos passados pelo nome.  Por exemplo, a seguinte `Display` chamada para o método exibe erro do compilador [BC30241: Argumento nomeado esperado](../../../misc/bc30241.md).

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

A partir do Visual Basic 15.5, os argumentos posicionais podem seguir argumentos nomeados se os argumentos posicionais finais estiverem na posição correta. Se compilado em Visual Basic 15.5, `Display` a chamada anterior para o método compila com sucesso e não gera mais erro do compilador [BC30241](../../../misc/bc30241.md).

Essa capacidade de misturar e combinar argumentos nomeados e posicionais em qualquer ordem é particularmente útil quando você deseja usar um argumento nomeado para tornar seu código mais legível. Por exemplo, `Person` o construtor de classe a `Person`seguir requer dois `Nothing`argumentos do tipo , ambos podem ser .

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

O uso de argumentos mistos e posicionais ajuda a tornar `father` `mother` clara a `Nothing`intenção do código quando o valor dos argumentos e argumentos é:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

Para seguir argumentos posicionais com argumentos nomeados, você deve\*adicionar o seguinte elemento ao seu arquivo Visual Basic (.vbproj):

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Para obter mais informações, [consulte a configuração da versão visual básica](../../../language-reference/configure-language-version.md)do idioma .

## <a name="restrictions-on-supplying-arguments-by-name"></a>Restrições ao fornecimento de argumentos por nome

Você não pode passar argumentos por nome para evitar inserir argumentos necessários. Você pode omiti-lo apenas os argumentos opcionais.

Você não pode passar uma matriz de parâmetros pelo nome. Isso porque quando você chama o procedimento, você fornece um número indefinido de argumentos separados por comma para a matriz de parâmetros, e o compilador não pode associar mais de um argumento com um único nome.

## <a name="see-also"></a>Confira também

- [Procedimentos](./index.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Como passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)
- [Passar argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md)
- [Parâmetros opcionais](./optional-parameters.md)
- [Matrizes de parâmetros](./parameter-arrays.md)
- [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md)
- [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
