---
title: "Níveis de acesso no Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- members [Visual Basic], accessing in Visual Basic
- Friend access modifier
- access levels, declared elements
- access levels
- access modifiers
- Public access modifier
- Protected access modifier
- Protected Friend access modifier
- Private access modifier
- declared elements [Visual Basic], access level
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 87e43ac7e813cece1179bdaf24c86fa62adcb438
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="access-levels-in-visual-basic"></a>Níveis de acesso no Visual Basic
O *nível de acesso* de um elemento declarado é a extensão da habilidade de acessá-lo, ou seja, o que o código tem permissão para ler ou gravar nele. Isso é determinado não apenas por como você declarar o elemento em si, mas também pelo nível de acesso do contêiner do elemento. Código que não é possível acessar um elemento contendo não pode acessar qualquer um de seus elementos contidos, mesmo aqueles declaradas como `Public`. Por exemplo, um `Public` variável em um `Private` estrutura pode ser acessada de dentro da classe que contém a estrutura, mas não de fora dessa classe.  
  
## <a name="public"></a>Público  
 O [pública](../../../../visual-basic/language-reference/modifiers/public.md) palavra-chave na instrução de declaração especifica que os elementos podem ser acessados de código em qualquer lugar no mesmo projeto, de outros projetos que referenciem o projeto e de qualquer assembly criado a partir do projeto. O código a seguir mostra um exemplo `Public` declaração.  
  
```  
Public Class classForEverybody  
```  
  
 Você pode usar `Public` apenas no nível de namespace ou módulo. Isso significa que você pode declarar um elemento público no nível de um arquivo de origem ou o espaço para nome, ou dentro de uma interface, módulo, classe ou estrutura, mas não em um procedimento.  
  
## <a name="protected"></a>Protegido  
 O [protegidos](../../../../visual-basic/language-reference/modifiers/protected.md) palavra-chave na instrução de declaração especifica que os elementos podem ser acessados somente de dentro da mesma classe ou de uma classe derivada dessa classe. O código a seguir mostra um exemplo `Protected` declaração.  
  
```  
Protected Class classForMyHeirs  
```  
  
 Você pode usar `Protected` somente a classe nível e somente quando você declarar um membro de uma classe. Isso significa que você pode declarar um elemento protegido em uma classe, mas não no nível de um namespace ou arquivo de origem, ou dentro de uma interface, módulo, estrutura ou procedimento.  
  
## <a name="friend"></a>Friend  
 O [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) palavra-chave na instrução de declaração especifica que os elementos podem ser acessados de dentro do mesmo assembly, mas não de fora do assembly. O código a seguir mostra um exemplo `Friend` declaração.  
  
```  
Friend stringForThisProject As String  
```  
  
 Você pode usar `Friend` apenas no nível de namespace ou módulo. Isso significa que você pode declarar um elemento público no nível de um arquivo de origem ou o espaço para nome, ou dentro de uma interface, módulo, classe ou estrutura, mas não em um procedimento.  
  
## <a name="protected-friend"></a>Friend protegido  
 O `Protected` e `Friend` palavras-chave juntos na instrução de declaração especificam que os elementos podem ser acessados de classes derivadas ou dentro do mesmo assembly, ou ambos. O código a seguir mostra um exemplo `Protected Friend` declaração.  
  
```  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 Você pode usar `Protected Friend` somente a classe nível e somente quando você declarar um membro de uma classe. Isso significa que você pode declarar um elemento público em uma classe, mas não no nível de um namespace ou arquivo de origem, ou dentro de uma interface, módulo, estrutura ou procedimento.  
  
## <a name="private"></a>Particular  
 O [privada](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave na instrução de declaração especifica que os elementos podem ser acessados somente de dentro do mesmo módulo, classe ou estrutura. O código a seguir mostra um exemplo `Private` declaração.  
  
```  
Private numberForMeOnly As Integer  
```  
  
 Você pode usar `Private` apenas no nível de módulo. Isso significa que você pode declarar um elemento particular dentro de um módulo, classe ou estrutura, mas não no nível de um arquivo de origem ou namespace, dentro de uma interface ou em um procedimento.  
  
 No nível de módulo, o `Dim` instrução sem quaisquer palavras-chave de nível de acesso é equivalente a um `Private` declaração. No entanto, talvez você queira usar o `Private` palavra-chave para tornar o código mais fácil de ler e interpretar.  
  
## <a name="access-modifiers"></a>Modificadores de acesso  
 As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*. A tabela a seguir compara os modificadores de acesso.  
  
|Modificador de acesso|Nível de acesso concedido|Elementos que você pode declarar com esse nível de acesso|Contexto de declaração dentro do qual você pode usar esse modificador|  
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|  
|`Public`|Irrestrito:<br /><br /> Qualquer código que pode ver um elemento público pode acessá-lo|Interfaces<br /><br /> Módulos<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Membros de estrutura<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Arquivo de origem<br /><br /> Namespace<br /><br /> Interface<br /><br /> Módulo<br /><br /> Classe<br /><br /> Estrutura|  
|`Protected`|Derivacionais:<br /><br /> A classe que declara um elemento protegido, ou uma classe derivada, pode acessar o elemento de código|Interfaces<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Classe|  
|`Friend`|Assembly:<br /><br /> O código no assembly que declara que um elemento de amigo pode acessá-lo|Interfaces<br /><br /> Módulos<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Membros de estrutura<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Arquivo de origem<br /><br /> Namespace<br /><br /> Interface<br /><br /> Módulo<br /><br /> Classe<br /><br /> Estrutura|  
|`Protected` `Friend`|União de `Protected` e `Friend`:<br /><br /> O código na mesma classe ou o mesmo assembly como um elemento amigo protegido, ou em qualquer classe derivada da classe do elemento, pode acessá-lo|Interfaces<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Classe|  
|`Private`|Contexto de declaração:<br /><br /> Código de tipo que declara um elemento particular, incluindo o código de tipos contidos, pode acessar o elemento|Interfaces<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Membros de estrutura<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Módulo<br /><br /> Classe<br /><br /> Estrutura|  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Estático](../../../../visual-basic/language-reference/modifiers/static.md)  
 [Nomes de Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Referências a Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Características do Elemento Declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Tempo de vida no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Como controlar a disponibilidade de uma variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)  
 [Variáveis](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
