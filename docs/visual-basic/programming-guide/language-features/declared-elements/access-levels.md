---
title: "Acessar níveis no Visual Basic | Documentos do Microsoft"
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
- members, accessing in Visual Basic
- Friend access modifier
- access levels, declared elements
- access levels
- access modifiers
- Public access modifier
- Protected access modifier
- Protected Friend access modifier
- Private access modifier
- declared elements, access level
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 34c61c0bbb50bdd05facaf76ae16a52273e6c7dd
ms.lasthandoff: 03/13/2017

---
# <a name="access-levels-in-visual-basic"></a>Níveis de acesso no Visual Basic
O *nível de acesso* de um elemento declarado é a extensão da habilidade de acessá-lo, ou seja, que código tem permissão para ler ou gravar nele. Isso é determinado não apenas por como você declarar o elemento em si, mas também pelo nível de acesso do contêiner do elemento. Código que não é possível acessar um elemento contendo não pode acessar qualquer de seus elementos contidos, mesmo aqueles declaradas como `Public`. Por exemplo, um `Public` variável em uma `Private` estrutura pode ser acessada de dentro da classe que contém a estrutura, mas não de fora dessa classe.  
  
## <a name="public"></a>Público  
 O [pública](../../../../visual-basic/language-reference/modifiers/public.md) palavra-chave na instrução de declaração especifica que os elementos podem ser acessados de código em qualquer lugar no mesmo projeto, de outros projetos que referenciem o projeto e de qualquer assembly compilado do projeto. O código a seguir mostra um exemplo `Public` declaração.  
  
```  
Public Class classForEverybody  
```  
  
 Você pode usar `Public` somente no nível de namespace ou módulo. Isso significa que você pode declarar um elemento público no nível de um arquivo de origem ou espaço para nome, ou dentro de uma interface, módulo, classe ou estrutura, mas não em um procedimento.  
  
## <a name="protected"></a>Protegido  
 O [protegido](../../../../visual-basic/language-reference/modifiers/protected.md) palavra-chave na instrução de declaração especifica que os elementos podem ser acessados somente de dentro da mesma classe, ou de uma classe derivada dessa classe. O código a seguir mostra um exemplo `Protected` declaração.  
  
```  
Protected Class classForMyHeirs  
```  
  
 Você pode usar `Protected` apenas a classe nível e somente quando você declara um membro de uma classe. Isso significa que você pode declarar um elemento público em uma classe, mas não no nível de um arquivo de origem ou espaço para nome, ou dentro de uma interface, módulo, estrutura ou procedimento.  
  
## <a name="friend"></a>Friend  
 O [amigo](../../../../visual-basic/language-reference/modifiers/friend.md) palavra-chave na instrução de declaração especifica que os elementos podem ser acessados de dentro do mesmo assembly, mas não de fora do assembly. O código a seguir mostra um exemplo `Friend` declaração.  
  
```  
Friend stringForThisProject As String  
```  
  
 Você pode usar `Friend` somente no nível de namespace ou módulo. Isso significa que você pode declarar um elemento público no nível de um arquivo de origem ou espaço para nome, ou dentro de uma interface, módulo, classe ou estrutura, mas não em um procedimento.  
  
## <a name="protected-friend"></a>Friend protegido  
 O `Protected` e `Friend` palavras-chave juntos na instrução de declaração especificam que os elementos podem ser acessados de classes derivadas ou dentro do mesmo assembly, ou ambos. O código a seguir mostra um exemplo `Protected``Friend` declaração.  
  
```  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 Você pode usar `Protected``Friend` apenas a classe nível e somente quando você declara um membro de uma classe. Isso significa que você pode declarar um elemento público em uma classe, mas não no nível de um arquivo de origem ou espaço para nome, ou dentro de uma interface, módulo, estrutura ou procedimento.  
  
## <a name="private"></a>Particular  
 O [particular](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave na instrução de declaração especifica que os elementos podem ser acessados somente de dentro do mesmo módulo, classe ou estrutura. O código a seguir mostra um exemplo `Private` declaração.  
  
```  
Private numberForMeOnly As Integer  
```  
  
 Você pode usar `Private` somente no nível de módulo. Isso significa que você pode declarar um elemento público dentro de um módulo, classe ou estrutura, mas não no nível de um arquivo fonte ou namespace, dentro de uma interface, ou em um procedimento.  
  
 No nível de módulo, o `Dim` instrução sem qualquer acesso de nível palavras-chave é equivalente a um `Private` declaração. No entanto, talvez você queira usar o `Private` palavra-chave para tornar o código mais fácil de ler e interpretar.  
  
## <a name="access-modifiers"></a>Modificadores de acesso  
 As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*. A tabela a seguir compara os modificadores de acesso.  
  
|Modificador de acesso|Nível de acesso concedido|Elementos que você pode declarar com esse nível de acesso|Contexto de declaração dentro do qual você pode usar esse modificador|  
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|  
|`Public`|Irrestrito:<br /><br /> Qualquer código que possa ver um elemento público pode acessá-lo|Interfaces<br /><br /> Módulos<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Membros de estrutura<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Arquivo de origem<br /><br /> espaço de nome<br /><br /> Interface<br /><br /> Módulo<br /><br /> Classe<br /><br /> Estrutura|  
|`Protected`|Derivacionais:<br /><br /> A classe que declara um elemento protegido, ou uma classe derivada dele, pode acessar o elemento de código|Interfaces<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Classe|  
|`Friend`|Assembly:<br /><br /> O código no assembly que declara que um elemento de amigo pode acessá-lo|Interfaces<br /><br /> Módulos<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Membros de estrutura<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Arquivo de origem<br /><br /> espaço de nome<br /><br /> Interface<br /><br /> Módulo<br /><br /> Classe<br /><br /> Estrutura|  
|`Protected` `Friend`|União de `Protected` e `Friend`:<br /><br /> O código na mesma classe ou o mesmo assembly como um elemento amigo protegido, ou em qualquer classe derivada da classe do elemento, pode acessá-lo|Interfaces<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Classe|  
|`Private`|Contexto de declaração:<br /><br /> Código de tipo que declara um elemento particular, incluindo o código de tipos contidos, pode acessar o elemento|Interfaces<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Membros de estrutura<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Módulo<br /><br /> Classe<br /><br /> Estrutura|  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Estático](../../../../visual-basic/language-reference/modifiers/static.md)   
 [Nomes de elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Características do elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Tempo de vida no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Como: controlar a disponibilidade de uma variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)   
 [Variáveis](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
