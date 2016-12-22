---
title: "Diferen&#231;as entre sombreamento e sobreposi&#231;&#227;o (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "substituição, x sombreamento"
  - "sombreamento, x substituição"
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Diferen&#231;as entre sombreamento e sobreposi&#231;&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Quando você define uma classe que herda de uma classe base, você às vezes quer redefinir um ou mais elementos da classe base na classe derivada.  Sombreamento e sobrescrição estão disponíveis para esse propósito.  
  
## Comparação  
 Sombreamento e substituindo forem usadas quando herda de uma classe derivada de uma classe base, e ambos redefinir um elemento declarado com o outro.  Mas existem diferenças significantes entre os dois.  
  
 A seguinte tabela compara sombreamento com sobrescrição.  
  
||||  
|-|-|-|  
|Ponto de comparação|Sombreamento|Substituição|  
|Objetivo|Protege contra uma mudança subsequente na classe base que introduz um membro que você já definiu na classe base.|Permite polimorfismo através da definição de uma implementação de um procedimento ou propriedade com a mesma sequência de chamada <sup>1</sup>.|  
|Elemento redefinido|Qualquer tipo de elemento declarado|Somente um procedimento \(`Function`, `Sub`, ou `Operator`\) ou propriedade|  
|Elemento redefinido|Qualquer tipo de elemento declarado|Somente um procedimento ou propriedade com uma sequência de chamada idêntica <sup>1</sup>|  
|Nível de acesso do elemento redefinido|Qualquer nível de acesso|Não pode mudar o nível de acesso do elemento sobrescrito|  
|Legibilidade de gravabilidade do elemento redefinido|Qualquer combinação|Não pode mudar a legibilidade ou gravabilidade de propriedades sobrescritas|  
|Controle da redefinição|O elemento da classe base não pode forçar ou proibir sombreamento|Elemnto da classe base pode especificar `MustOverride`, `NotOverridable`, ou `Overridable`|  
|Uso de palavras chave|`Shadows` recomendado na classe derivada, `Shadows` assumido se  `Shadows` nem `Overrides` estão especificados <sup>2</sup>.|`Overridable` ou `MustOverride` necessário na classe base `Overrides` necessário na classe derivada|  
|Herança do elemento redefinido em classes derivadas da classe derivada|Elememento sombreante herdado por classes derivadas posteriores; elemento sombreado ainda escondido <sup>3</sup>|Elemento sobrescritor herdado por futuras classes derivadas; elemento sobrescrito ainda sobrescrito|  
  
 <sup>1</sup> A *sequência de chamada* consiste do tipo de elemento\(`Function`, `Sub`, `Operator`, ou `Property`\), nome, listas de parâmetros e tipo da saída.  Você não pode sobrescrever um procedimento com uma propriedade, ou o contrário.  Você não pode sobrescrever nenhum tipo de procedimento  \(`Function`, `Sub`, ou `Operator`\) com outro tipo.  
  
 <sup>2</sup> Se você não especificar ou `Shadows` ou `Overrides`,  o compilador envia uma mensagem de aviso para ajudá\-lo a ter certeza de qual redefinição deseja usar.  Se você ignorar o aviso, o mecanismo de sombreamento é usado.  
  
 <sup>3</sup> Se o elemento sombreador é inacessível numa futura classe derivada, sombreamento não é herdado.  Por exemplo, se você declarar o elemento sombreador como `Private`, uma classe derivando de sua classe derivada herda ou elemento original em vez do elemento sombreador.  
  
## Diretrizes  
 Você normalmente usa sobrescrição nos seguintes casos:  
  
-   Você está definindo classes derivadas polimórficas.  
  
-   Você deseja a segurança de fazer o compilador forçar o mesmo tipo de elemento e sequência de chamada.  
  
 Você normalmente usa sombreamento nos seguintes casos:  
  
-   Você antecipa que sua classe base pode ser modificada e definir um elemento usando o mesmo nome que o seu.  
  
-   Você deseja a liberdade de mudar o tipo de elemento ou sequência de chamada.  
  
## Consulte também  
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Como ocultar uma variável com o mesmo nome que a variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)   
 [Como ocultar uma variável herdada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)   
 [Como acessar uma variável oculta por uma classe derivada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)   
 [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Substituições](../../../../visual-basic/language-reference/modifiers/overrides.md)