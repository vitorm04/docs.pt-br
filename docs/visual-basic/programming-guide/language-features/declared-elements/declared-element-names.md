---
title: Declarado como nomes de elemento (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declared elements, case sensitivity
- names, Visual Basic rules
- naming conventions
- element names
- declared elements, identifiers
- declarations, elements
- declared elements, valid names
- '[] escape characters [Visual Basic]'
- names, elements
- declaration statements, declared elements
- declaring elements
- identifiers, declared elements
- case sensitivity, declared element names
- escape characters
- names, declared elements
- declared elements, about declared elements
- escaped names
- declared elements, names
- names, naming conventions
- identifiers, elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
caps.latest.revision: 27
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 56ac0684e5176f33aa6f9600f20d9fe3fcf09416
ms.lasthandoff: 03/13/2017

---
# <a name="declared-element-names-visual-basic"></a>Nomes de elemento declarados (Visual Basic)
Cada elemento declarado tem um nome, também chamado de um *identificador*, que é o código que se usa para se referir a ele.  
  
## <a name="rules"></a>Regras  
 Um nome de elemento em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] deve observar as seguintes regras:  
  
-   Ele deve começar com um caractere alfabético ou sublinhado (`_`).  
  
-   Ele deve conter apenas caracteres alfabéticos, dígitos decimais e sublinhados.  
  
-   Ele deve conter pelo menos um caractere alfabético ou dígito decimal se ele começa com um sublinhado.  
  
-   Ele não deve ter mais de 1023 caracteres.  
  
 O limite de 1023 caracteres também se aplica a cadeia de caracteres inteira de um nome totalmente qualificado, como `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.  
  
 O exemplo a seguir mostra alguns nomes de elemento válido.  
  
 `aB123__45`  
  
 `_567`  
  
 O exemplo a seguir mostra alguns nomes de elemento inválido. O primeiro contém somente um sublinhado, o segundo começa com um dígito decimal e o terceiro contém um caractere inválido ($).  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  Nomes de elementos iniciados com um sublinhado (`_`) não fazem parte do [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), então um código compatível com CLS não pode usar um componente que define tais nomes. No entanto, um sublinhado em qualquer outra posição de um nome de elemento é compatível com CLS.  
  
### <a name="name-length-guidelines"></a>Diretrizes para comprimento de nome  
 Como uma questão prática, o nome deve ser tão curta quanto possível e ainda identificar claramente a natureza do elemento. Isso melhora a legibilidade do código e reduz o tamanho de arquivo de origem e de comprimento de linha.  
  
 Por outro lado, o nome não deve ser tão curto que ele não descreve adequadamente o elemento que representa e como seu código usa. Isso é importante para a legibilidade do código. Se alguém está tentando compreendê-la, ou se você mesmo o está examinando muito tempo depois que você o escreveu, nomes de elementos adequados podem salvar uma quantidade considerável de tempo.  
  
## <a name="escaped-names"></a>Nomes de escape  
 Geralmente, um nome de elemento não deve conter qualquer uma das palavras-chave reservadas pelo [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], como `Case` ou `Friend`. No entanto, você pode definir um *nome escapado*, que é colocado entre colchetes (`[ ]`). Um nome escapado pode conter qualquer [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] palavra-chave, pois os colchetes removem qualquer ambiguidade. Você também usa os colchetes quando você se referir ao nome posteriormente no seu código.  
  
 Em geral, você deve usar nomes escapados apenas quando:  
  
-   Seu código migrou de uma versão anterior do [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] que não reservar a palavra-chave que está sendo usada como um nome; ou  
  
-   Você está trabalhando com código escrito em outra linguagem na qual a palavra-chave fornecida não está reservada.  
  
 Caso contrário, considere renomear o elemento se seu nome está em conflito com uma palavra-chave. O ambiente de desenvolvimento integrado (IDE) fornece uma maneira fácil de fazer isso. Para obter mais informações, consulte [refatoração](https://docs.microsoft.com/visualstudio/vb-ide/refactoring-vb).  
  
## <a name="case-sensitivity-in-names"></a>Diferenciação de maiusculas e minúsculas em nomes  
 Nomes de elementos em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] diferenciam maiusculas de minúsculas. Isso significa que quando o compilador compara dois nomes que diferem somente no caso alfabético, ele interpreta como o mesmo nome. Por exemplo, ele considera `ABC` e `abc` para referir-se ao mesmo elemento declarado.  
  
 No entanto, o common language runtime (CLR) usa associação diferencia maiusculas de minúsculas. Portanto, quando você gerar um assembly ou uma DLL e disponibilizá-lo para outros assemblies, seus nomes não diferenciam maiusculas de minúsculas. Por exemplo, se você definir uma classe com um elemento chamado `ABC`, e outros assemblies fazer uso de sua classe por meio do common language runtime, eles devem se referir ao elemento como `ABC`. Se você posteriormente recompilar sua classe e alterar o nome do elemento para `abc`, os outros assemblies usando sua classe não podem acessar esse elemento. Portanto, quando você lançar uma versão atualizada de um assembly, você não deve alterar maiusculas e minúsculas em quaisquer elementos públicos.  
  
## <a name="names-and-locales"></a>Nomes e locais  
 Comparação de nomes é independente da localidade. Se dois nomes correspondem em uma localidade, eles são garantidos para corresponder em todas as localidades.  
  
## <a name="see-also"></a>Consulte também  
 [Elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)   
 [Características do elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Instruções](../../../../visual-basic/language-reference/statements/index.md)
