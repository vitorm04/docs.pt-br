---
title: "Como controlar a disponibilidade de uma vari&#225;vel (Visual Basic) | Microsoft Docs"
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
  - "níveis de acesso, elementos declarados"
  - "níveis de acesso, variáveis"
  - "elementos declarados, nível de acesso"
  - "palavra-chave Friend, acessando variáveis"
  - "palavra-chave Private, acessando variáveis"
  - "palavra-chave Protected, acessando variáveis"
  - "palavra-chave Public, acessando variáveis"
  - "variáveis [Visual Basic], nível de acesso"
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como controlar a disponibilidade de uma vari&#225;vel (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você controla a disponibilidade de uma variável especificando seu  *nível de acesso*.  O nível de acesso determina que código tem permissão para ler ou gravar a variável.  
  
-   *Variáveis de membro* \(definido no nível de módulo e fora de qualquer procedimento\) padrão para acesso público, o que significa que qualquer código que pode vê\-los pode acessá\-los.  Você pode alterar isso, especificando um modificador de acesso.  
  
-   *Variáveis locais* \(definido dentro de um procedimento\) nominally têm o acesso do público, embora apenas o código dentro do seu procedimento pode acessá\-los.  Você não pode alterar o nível de acesso de uma variável local, mas você pode alterar o nível de acesso do procedimento que o contém.  
  
 Para obter mais informações, consulte [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## Particular e o acesso público  
  
#### Para fazer uma variável acessível somente dentro de seu módulo, classe ou estrutura  
  
1.  Local do [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) para a variável dentro do módulo, classe ou estrutura, mas fora de qualquer procedimento.  
  
2.  Inclua a palavra\-chave [Particular](../../../../visual-basic/language-reference/modifiers/private.md) na instrução `Dim`.  
  
     Você pode ler ou gravar a variável de qualquer lugar dentro do módulo, classe ou estrutura, mas não de fora dela.  
  
#### Para fazer uma variável acessível a partir de qualquer código que pode vê\-lo  
  
1.  Para uma variável de membro, coloque o `Dim` a declaração da variável dentro de um módulo, classe ou estrutura, mas fora de qualquer procedimento.  
  
2.  Inclua a palavra\-chave [Público](../../../../visual-basic/language-reference/modifiers/public.md) na instrução `Dim`.  
  
     Você pode ler ou gravar a variável a partir de qualquer código que interopera com seu conjunto.  
  
 \- ou \-  
  
1.  Para uma variável local, coloque o `Dim` a declaração da variável dentro de um procedimento.  
  
2.  Não inclua o `Public` palavra\-chave na `Dim` instrução.  
  
     Você pode ler ou gravar a variável de qualquer lugar dentro do procedimento, mas não de fora dela.  
  
## Protegido e acesso Friend  
 Você pode limitar o nível de acesso de uma variável para a sua classe e as classes derivadas, ou para seu assembly.  Você também pode especificar a união entre essas limitações, que permite o acesso do código em qualquer classe derivada ou em qualquer outro local no mesmo assembly.  Você especifica essa união combinando o `Protected` e `Friend` as palavras\-chave na mesma declaração.  
  
#### Para fazer uma variável acessível somente dentro de sua classe e de quaisquer classes derivadas  
  
1.  Local do `Dim` a declaração da variável dentro de uma classe, mas fora de qualquer procedimento.  
  
2.  Inclua a palavra\-chave [Protegido](../../../../visual-basic/language-reference/modifiers/protected.md) na instrução `Dim`.  
  
     Você pode ler ou gravar à variável de qualquer lugar dentro da classe, bem como de dentro de qualquer classe derivada dela, mas não de fora de qualquer classe da cadeia de derivação.  
  
#### Para fazer uma variável acessível somente dentro do mesmo assembly.  
  
1.  Local do `Dim` a declaração da variável dentro de um módulo, classe ou estrutura, mas fora de qualquer procedimento.  
  
2.  Inclua a palavra\-chave [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) na instrução `Dim`.  
  
     Você pode ler ou gravar a variável de qualquer lugar dentro do módulo, classe ou estrutura, bem como de qualquer código no mesmo assembly, mas não de fora do assembly.  
  
## Exemplo  
 O exemplo a seguir mostra a declarações de variáveis com `Public`, `Protected`, `Friend`, `Protected Friend`, e `Private` níveis de acesso.  Observe que quando o `Dim` declaração especifica um nível de acesso, você não precisa incluir o `Dim` palavra\-chave.  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## Segurança do .NET Framework  
 Quanto mais restritivo o nível de acesso de uma variável, quanto menores as chances de que um código mal\-intencionado pode tornar impróprio usá\-lo.  
  
## Consulte também  
 [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Público](../../../../visual-basic/language-reference/modifiers/public.md)   
 [Protegido](../../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)   
 [Particular](../../../../visual-basic/language-reference/modifiers/private.md)