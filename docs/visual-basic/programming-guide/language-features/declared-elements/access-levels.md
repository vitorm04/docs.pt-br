---
title: "N&#237;veis de acesso no Visual Basic | Microsoft Docs"
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
  - "níveis de acesso"
  - "níveis de acesso, elementos declarados"
  - "modificadores de acesso"
  - "elementos declarados, nível de acesso"
  - "modificador de acesso Friend"
  - "membros, acessando no Visual Basic"
  - "Modificador de acesso privado"
  - "Modificador de acesso protegido"
  - "Modificador de acesso Friend protegido"
  - "Modificador de acesso público"
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#237;veis de acesso no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O  *o nível de acesso* de um elemento declarado é a extensão da habilidade de acessá\-lo, ou seja, o que o código tem permissão para ler ou gravar nela.  Isso é determinado não apenas por como você declarar o elemento em si, mas também pelo nível de acesso do recipiente do elemento.  O código que não é possível acessar um elemento contendo não pode acessar qualquer de seus elementos contidos, mesmo aqueles declaradas como `Public`.  Por exemplo, uma `Public` variável em uma `Private` estrutura pode ser acessada de dentro da classe que contém a estrutura, mas não de fora dessa classe.  
  
## Público  
 A [Público](../../../../visual-basic/language-reference/modifiers/public.md) palavra\-chave na instrução de declaração especifica que os elementos podem ser acessados a partir de código em qualquer lugar no mesmo projeto, de outros projetos que fazem referência do projeto, e do qualquer conjunto de módulos \(assembly\) criado a partir do projeto.  O código a seguir mostra um exemplo `Public` Declaração.  
  
```  
Public Class classForEverybody  
```  
  
 Você pode usar `Public` somente em nível de namespace ou módulo.  Isso significa que você pode declarar um elemento público no nível de uma arquivo de origem ou namespace, ou dentro de uma interface, módulo, de classe ou estrutura, mas não em um procedimento.  
  
## Protegido  
 A [Protegido](../../../../visual-basic/language-reference/modifiers/protected.md) palavra\-chave na instrução de declaração especifica que os elementos podem ser acessados somente de dentro da mesma classe, ou de uma classe derivada dessa classe.  O código a seguir mostra um exemplo `Protected` Declaração.  
  
```  
Protected Class classForMyHeirs  
```  
  
 Você pode usar `Protected` somente no nível de classe, e somente quando você declarar um membro da classe.  Isso significa que você pode declarar um elemento público no nível de uma arquivo de origem ou namespace, ou dentro de uma interface, módulo, de classe ou estrutura, mas não em um procedimento.  
  
## Friend  
 A [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) palavra\-chave na instrução de declaração especifica que os elementos podem ser acessados a partir dentro mesmo assembly, mas não de fora o assembly.  O código a seguir mostra um exemplo `Friend` Declaração.  
  
```  
Friend stringForThisProject As String  
```  
  
 Você pode usar `Friend` somente em nível de namespace ou módulo.  Isso significa que você pode declarar um elemento público no nível de uma arquivo de origem ou namespace, ou dentro de uma interface, módulo, de classe ou estrutura, mas não em um procedimento.  
  
## Amigo Protegido  
 O `Protected` e especifica se os elementos podem ser acessados de classes derivadas ou dentro de `Friend` palavras\-chave juntos na instrução de declaração o mesmo conjunto de módulos \(assembly\), ou ambos.  O código a seguir mostra um exemplo `Protected``Friend` declaração.  
  
```  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 Você pode usar `Protected``Friend` somente à classe de nível e somente quando você declara um membro de uma classe.  Isso significa que você pode declarar um elemento público no nível de uma arquivo de origem ou namespace, ou dentro de uma interface, módulo, de classe ou estrutura, mas não em um procedimento.  
  
## Private  
 A [Particular](../../../../visual-basic/language-reference/modifiers/private.md) palavra\-chave na instrução de declaração especifica que os elementos podem ser acessados somente de dentro da mesma classe, ou de uma classe derivada dessa classe.  O código a seguir mostra um exemplo `Private` Declaração.  
  
```  
Private numberForMeOnly As Integer  
```  
  
 Você pode usar `Private` somente no nível de módulo.  Isso significa que você pode declarar um elemento público no nível de uma arquivo de origem ou namespace, ou dentro de uma interface, módulo, de classe ou estrutura, mas não em um procedimento.  
  
 No nível de módulo, a instrução `Dim` sem qualquer acesso de nível palavras\-chave é equivalente a uma declaração `Private`.  No entanto, convém usar a `Private` palavra\-chave para tornar o código mais fácil de ler e interpretar.  
  
## Modificadores de acesso  
 As palavras\-chave que especificam o nível de acesso são chamadas  *modificadores*  acesso.  A tabela a seguir compara os modificadores de acesso.  
  
|Modificador de acesso|Acesso concedido nível|Elementos você pode declarar com esse nível de acesso|Declaração de contexto no qual você pode usar esse modificador|  
|---------------------------|----------------------------|-----------------------------------------------------------|--------------------------------------------------------------------|  
|`Public`|Irrestrito:<br /><br /> Qualquer código que possa ver um elemento público pode acessá\-lo|Interfaces<br /><br /> Módulos<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Membros de estrutura<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Arquivo fonte<br /><br /> Namespace<br /><br /> Interface<br /><br /> Module<br /><br /> Classe<br /><br /> Estrutura|  
|`Protected`|Derivacional:<br /><br /> Código na classe que declara um elemento protegido, ou uma classe derivada dele, pode acessar o elemento|Interfaces<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Classe|  
|`Friend`|Conjunto de módulos:<br /><br /> Código no conjunto de módulos \(assembly\) que declara que um elemento de amigo pode acessá\-lo|Interfaces<br /><br /> Módulos<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Membros de estrutura<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Arquivo fonte<br /><br /> Namespace<br /><br /> Interface<br /><br /> Module<br /><br /> Classe<br /><br /> Estrutura|  
|`Protected` `Friend`|União de `Protected` e `Friend`:<br /><br /> Código na mesma classe ou o mesmo conjunto como um elemento Amigo Protegido, ou em qualquer classe derivada da classe do elemento, pode acessá\-lo|Interfaces<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Classe|  
|`Private`|Contexto da Declaração.<br /><br /> Código de tipo que declara um elemento particular, incluindo o código de tipos contidos, pode acessar o elemento|Interfaces<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Membros de estrutura<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Module<br /><br /> Classe<br /><br /> Estrutura|  
  
## Consulte também  
 [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Estático](../../../../visual-basic/language-reference/modifiers/static.md)   
 [Nomes de elemento declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Características do elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Tempo de vida no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Como controlar a disponibilidade de uma variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)   
 [Variáveis](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [Declaração de variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)