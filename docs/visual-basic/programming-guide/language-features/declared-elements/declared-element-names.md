---
title: "Nomes de elemento declarados (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "caracteres de escape [] [Visual Basic]"
  - "diferenciação de maiúsculas e minúsculas, nomes de elementos declarados"
  - "instruções de declaração, elementos declarados"
  - "declarações, elementos"
  - "elementos declarados, sobre elementos declarados"
  - "elementos declarados, diferenciação de maiúsculas e minúsculas"
  - "elementos declarados, identificadores"
  - "elementos declarados, nomes"
  - "elementos declarados, nomes válidos"
  - "declarando elementos"
  - "nomes de elementos"
  - "caracteres de escape"
  - "nomes seguidos por caracteres de escape"
  - "identificadores, elementos declarados"
  - "identificadores, elementos"
  - "nomes, elementos declarados"
  - "nomes, elementos"
  - "nomes, convenções de nomenclatura"
  - "nomes, regras do Visual Basic"
  - "convenções de nomenclatura"
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nomes de elemento declarados (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Cada elemento declarado tem um nome, também chamado de *identificador*, que é o código que se usa para se referir a ele.  
  
## Regras  
 Um nome de elemento em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] deve observar as seguintes regras:  
  
-   Ele deve começar com um caractere alfabético ou um sublinhado \(`_`\).  
  
-   Ele deve conter apenas caracteres alfabéticos, dígitos decimais e sublinhados.  
  
-   Ele deve conter pelo menos um caractere alfabético ou dígito decimal se ele começa com um sublinhado.  
  
-   Ele não deve ter mais de 1023 caracteres.  
  
 O limite de 1023 caracteres também se aplica a toda a sequência de caracteres de uma nome totalmente qualificado, como `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.  
  
 O exemplo a seguir mostra alguns nomes válidos de elemento.  
  
 `aB123__45`  
  
 `_567`  
  
 O exemplo a seguir mostra alguns nomes inválidos de elemento.  O primeiro contém somente um sublinhado, o segundo começa com um dígito decimal e o terceiro contém um caractere inválido \($\).  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  Nomes de elementos iniciados com um sublinhado \(`_`\) não fazem parte do [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), de modo que o código compatível com CLS não pode usar um componente que define tais nomes.  No entanto, um sublinhado em qualquer outra posição de um nome de elemento é compatível com CLS.  
  
### Diretrizes para Comprimento de Nomes  
 Como uma questão prática, o nome deve ser tão breve quanto possível e ainda identificar claramente a natureza do elemento.  Isso melhora a legibilidade do código e reduz o comprimento da linha e o tamanho do arquivo\-fonte.  
  
 Por outro lado, o seu nome não deve ser tão curto a ponto de não descrever adequadamente o elemento que representa e como o código o usa.  Isso é importante para a legibilidade do código.  Se mais alguém está tentando compreendê\-lo, ou se você mesmo o está examinando muito tempo depois que você o escreveu, nomes de elementos adequados podem salvar uma quantidade considerável de tempo.  
  
## Nomes Escapados  
 Geralmente, um nome de elemento não deve conter qualquer uma das palavras\-chave reservadas pelo [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], como `Case` ou `Friend`.  No entanto, você pode definir um *nome escapado*, que é colocado entre colchetes \(`[ ]`\).  Um nome escapado pode conter qualquer palavra\-chave [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], pois os colchetes removem qualquer ambiguidade.  Você também usa os colchetes quando você se referir ao nome posteriormente no seu código.  
  
 Em geral, você deve usar nomes escapados apenas quando:  
  
-   Seu código migrou de uma versão anterior do [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] que não reservava a palavra\-chave que está sendo usada como um nome; ou  
  
-   Você está trabalhando com código escrito em outra linguagem na qual a palavra\-chave em questão não é reservada.  
  
 Caso contrário, considere renomear o elemento se seu nome entrar em conflito com uma palavra\-chave.  O ambiente de desenvolvimento integrado \(IDE, integrated development environment\) fornece uma maneira fácil para fazer isso.  Para obter mais informações, consulte [Caixa de diálogo Refatoração e Renomear](../../../../visual-basic/developing-apps/using-ide/refactoring-and-rename-dialog-box.md).  
  
## Sensibilidade a Maiúsculas em Nomes  
 Nomes de elementos em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não diferenciam maiúsculas de minúsculas.  Isso significa que quando o compilador compara dois nomes que diferem somente no uso de maiúsculas e minúsculas, ele os interpreta como o mesmo nome.  Por exemplo, ele considera que `ABC` e `abc` referem\-se ao mesmo elemento declarado.  
  
 No entanto, a Linguagem Comum em Tempo de Execução \(CLR, common language runtime\) usa vinculação que diferencia maiúsculas e minúsculas.  Portanto, quando você produzir um conjunto de módulos \(assembly\) ou uma DLL e disponibilizá\-lo a outros conjuntos de módulos \(assemblies\), seus nomes não são mais indiferentes a maiúsculas e minúsculas.  Por exemplo, se você definir uma classe com um elemento chamado `ABC`, e fizer com que outros conjuntos usem sua classe por meio da Linguagem Comum em Tempo de Execução, eles devem se referir ao elemento como `ABC`.  Se você posteriormente recompilar sua classe e alterar nome do elemento para `abc`, os outros conjuntos de módulos \(assemblies\) usando sua classe não mais poderão acessar esse elemento.  Portanto, quando você lançar uma versão atualizada de um conjunto de módulos \(assembly\), você não deve alterar maiúsculas e minúsculas em quaisquer elementos públicos.  
  
## Nomes e Locais  
 Comparação de nomes é independente da localidade.  Se dois nomes correspondem em uma localidade, eles coincidem em todas as localidades.  
  
## Consulte também  
 [Elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)   
 [Características do elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Instruções](../../../../visual-basic/language-reference/statements/index.md)