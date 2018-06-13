---
title: Nomes de elemento declarados (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
ms.openlocfilehash: 2f48f885b66f99ecc8c6c7e13fea7e75f0e3d24a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651473"
---
# <a name="declared-element-names-visual-basic"></a>Nomes de elemento declarados (Visual Basic)
Cada elemento declarado tem um nome, também chamado de um *identificador*, que é o código que se usa para se referir a ele.  
  
## <a name="rules"></a>Regras  
 Um nome de elemento no Visual Basic deve observar as regras a seguir:  
  
-   Ele deve começar com um caractere alfabético ou sublinhado (`_`).  
  
-   Ele deve conter apenas caracteres alfabéticos, dígitos decimais e sublinhados.  
  
-   Ele deve conter pelo menos um caractere alfabético ou dígito decimal se ele começa com um sublinhado.  
  
-   Ele não deve ter mais de 1.023 caracteres.  
  
 O limite de 1023 caracteres também se aplica à cadeia de caracteres inteira de um nome totalmente qualificado, como `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.  
  
 O exemplo a seguir mostra alguns nomes de elemento válido.  
  
 `aB123__45`  
  
 `_567`  
  
 O exemplo a seguir mostra alguns nomes de elemento inválido. O primeiro contém somente um sublinhado, o segundo começa com um dígito decimal e o terceiro contém um caractere inválido ($).  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  Nomes de elementos iniciados com um sublinhado (`_`) não fazem parte do [independência da linguagem e componentes independentes da linguagem](../../../../standard/language-independence-and-language-independent-components.md) (CLS), então um código compatível com CLS não pode usar um componente que define tais nomes. No entanto, um sublinhado em qualquer outra posição de um nome de elemento é compatível com CLS.  
  
### <a name="name-length-guidelines"></a>Diretrizes para comprimento de nome  
 De forma prática, o nome deve ser tão curto quanto possível e ainda identificar claramente a natureza do elemento. Isso melhora a legibilidade do código e reduz o tamanho de arquivo de origem e de comprimento de linha.  
  
 Por outro lado, o nome não deve ser tão curto que ele não descreve adequadamente o elemento que representa e como seu código usa. Isso é importante para a legibilidade do código. Se alguém está tentando compreendê-la, ou se você mesmo o está examinando muito tempo depois que você o escreveu, nomes de elementos adequados podem salvar uma quantidade considerável de tempo.  
  
## <a name="escaped-names"></a>Nomes de escape  
 Geralmente, um nome de elemento não deve conter qualquer uma das palavras-chave reservadas pelo Visual Basic, como `Case` ou `Friend`. No entanto, você pode definir um *nome escapado*, que é colocado entre colchetes (`[ ]`). Um nome escapado pode corresponder a qualquer palavra-chave do Visual Basic, pois os colchetes removem qualquer ambiguidade. Você também usa os colchetes quando você se referir ao nome posteriormente no seu código.  
  
 Em geral, você deve usar nomes escapados apenas quando:  
  
-   O código foi migrado de uma versão anterior do Visual Basic que não reservar a palavra-chave que está sendo usada como um nome; ou  
  
-   Você está trabalhando com código escrito em outra linguagem na qual a palavra-chave fornecida não está reservada.  
  
 Caso contrário, considere renomear o elemento se seu nome está em conflito com uma palavra-chave. O ambiente de desenvolvimento integrado (IDE) fornece uma maneira fácil de fazer isso. Para obter mais informações, consulte [refatoração](/visualstudio/vb-ide/refactoring-vb).  
  
## <a name="case-sensitivity-in-names"></a>Diferenciação de maiusculas e minúsculas em nomes  
 Nomes de elementos no Visual Basic diferenciam maiusculas de minúsculas. Isso significa que quando o compilador compara dois nomes que diferem somente no caso alfabético, ele interpreta como o mesmo nome. Por exemplo, ele considera `ABC` e `abc` para se referir ao mesmo elemento declarado.  
  
 No entanto, o common language runtime (CLR) usa associação diferencia maiusculas de minúsculas. Portanto, quando você produzir um assembly ou uma DLL e disponibilizá-lo para outros assemblies, seus nomes não diferenciam maiusculas de minúsculas. Por exemplo, se você definir uma classe com um elemento chamado `ABC`, e outros assemblies fazer uso de sua classe por meio do common language runtime, eles devem se referir ao elemento como `ABC`. Se você posteriormente recompilar sua classe e alterar o nome do elemento para `abc`, os outros assemblies usando a classe não podem acessar esse elemento. Portanto, quando você solta uma versão atualizada de um assembly, você não deve alterar maiusculas e minúsculas em quaisquer elementos públicos.  
  
## <a name="names-and-locales"></a>Nomes e locais  
 Comparação de nomes é independente da localidade. Se dois nomes correspondem em uma localidade, eles são garantidos para corresponder em todas as localidades.  
  
## <a name="see-also"></a>Consulte também  
 [Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 [Características do Elemento Declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Referências a Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Instruções](../../../../visual-basic/language-reference/statements/index.md)
