---
title: "Declara&#231;&#227;o de vari&#225;vel no Visual Basic | Microsoft Docs"
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
  - "variáveis [Visual Basic], declarando"
  - "variáveis de membro, declarações"
  - "Instrução Dim, a declaração de variável"
  - "declarando variáveis"
  - "variáveis [Visual Basic], escopo"
  - "variáveis [Visual Basic], tipos de dados"
  - "tipos de dados [Visual Basic], declarações de variável"
  - "tempo de vida, variáveis"
  - "variáveis [Visual Basic], tempo de vida"
  - "níveis de acesso, variáveis"
  - "escopo, as instruções de declaração"
  - "variáveis [Visual Basic], nível de acesso"
  - "variáveis locais, declarações"
  - "escopo de variáveis"
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
caps.latest.revision: 31
caps.handback.revision: 31
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Declara&#231;&#227;o de vari&#225;vel no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você declara uma variável para especificar seu nome e características.  A instrução de declaração para variáveis é [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).  Seu conteúdo local e determinam as características da variável.  
  
 Regras para considerações e variáveis de nomeação, consulte [Nomes de elemento declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## Níveis de declaração  
  
### Variáveis locais e de membro  
 *Uma variável local* é um que é declarado dentro de um procedimento.  *Um variável de membro* é um membro de um tipo de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ; é declarado no nível de módulo, dentro de uma classe, estrutura, ou módulo, mas não dentro de qualquer procedimento interno que a classe, estrutura, módulo ou.  
  
### Compartilhado e variáveis de instância  
 Em uma classe ou estrutura, a categoria de um variável de membro depende se está compartilhado.  Se é declarada com a palavra\-chave de [Compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md) , é *uma variável compartilhada*, e existe em uma única cópia compartilhado entre todas as instâncias da classe ou estrutura.  
  
 Se não for *uma variável de instância*, e uma cópia separada de ela é criada para cada instância da classe ou estrutura.  Uma cópia receberá de uma variável de instância está disponível somente para a instância da classe ou estrutura na qual foi criado.  É independente de uma cópia da variável de instância em qualquer outra instância da classe ou estrutura.  
  
## Declarando o tipo de dados  
 A cláusula de [Como](../../../../visual-basic/language-reference/statements/as-clause.md) na instrução de declaração permite que você defina o tipo de dados ou tipo de objeto de variável que é declarado.  Você pode especificar qualquer um dos seguintes tipos para uma variável:  
  
-   Um tipo de dados elementar, como `Boolean`, `Long`, ou `Decimal`  
  
-   Um tipo de dados composto, como uma matriz ou estrutura  
  
-   Um tipo de objeto, ou a classe, definidos no seu aplicativo ou em outro aplicativo  
  
-   Uma classe de [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] , como <xref:System.Windows.Forms.Label> ou <xref:System.Windows.Forms.TextBox>  
  
-   Um tipo de interface, como <xref:System.IComparable> ou <xref:System.IDisposable>  
  
 Você pode declarar diversas variáveis em uma instrução sem ter que repetir o tipo de dados.  Nas instruções a seguir, variáveis `i`, `j`, e `k` são declarados como o tipo `Integer`, `l` e `m` como `Long`, e `x` e `y` como `Single`:  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 Para obter mais informações, sobre tipos de dados, consulte [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md) .  Para obter mais informações sobre objetos, consulte [Objetos e classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) e [Programming with Components](../Topic/Programming%20with%20Components.md).  
  
## Inferência de tipos local  
 *Inferência de tipos* é usada para determinar os tipos de dados de variáveis locais declaradas sem uma cláusula de `As` .  O compilador infere o tipo da variável do tipo da expressão de inicialização.  Isso permite que você declarar variáveis sem especificar explicitamente seu tipo.  No exemplo, `num1` e `num2` são altamente digitados como inteiros.  
  
 [!CODE [VbVbalrTypeInference#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrTypeInference#1)]  
  
 Se você desejar usar inferência de tipos local, `Option Infer` deve ser definido como `On`.  Para obter mais informações, consulte [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) e [Instrução Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## Características de variáveis declaradas  
 *O tempo de vida* de uma variável é o período de tempo em que está disponível para uso.  Normalmente, uma variável existe enquanto o elemento que declara\-lo \(como um procedimento ou uma classe\) continua a existir.  Se a variável não precisa continuar existindo além do tempo de vida do elemento que a contém, você não precisa fazer nada especial na declaração.  Se a variável precisa continuar existindo mais que o elemento que a contém, você pode incluir a palavra chave `Static` ou `Shared` na sua declaração `Dim`.  Para obter mais informações, consulte [Tempo de vida no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
 *O escopo* de uma variável é o conjunto de todo o código que pode fazer referência a ela sem qualificar seu nome.  O escopo de uma variável é determinado por onde é declarado.  O código localizado em uma determinada região pode usar variáveis definidos na região sem precisar qualificar seus nomes.  Para obter mais informações, consulte [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
 *O nível de acesso* de uma variável é a extensão de código que tem permissão para acessar.  Isso é determinado pelo modificador de acesso \(tal como [Público](../../../../visual-basic/language-reference/modifiers/public.md) ou [Particular](../../../../visual-basic/language-reference/modifiers/private.md)\) que você usa na declaração de `Dim` .  Para obter mais informações, consulte [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## Consulte também  
 [Como criar uma nova variável](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)   
 [Como inserir e remover dados de uma variável](../Topic/How%20to:%20Move%20Data%20Into%20and%20Out%20of%20a%20Variable%20\(Visual%20Basic\).md)   
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Protegido](../../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)   
 [Estático](../../../../visual-basic/language-reference/modifiers/static.md)   
 [Características do elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Instrução Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)