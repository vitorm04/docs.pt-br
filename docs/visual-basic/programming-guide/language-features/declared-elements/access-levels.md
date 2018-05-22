---
title: Níveis de acesso no Visual Basic
ms.date: 05/10/2018
helpviewer_keywords:
- members [Visual Basic], accessing in Visual Basic
- Friend access modifier
- access levels, declared elements
- access levels
- access modifiers
- Public access modifier
- Protected access modifier
- Protected Friend access modifier
- Private Protected access modifier
- Private access modifier
- declared elements [Visual Basic], access level
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
ms.openlocfilehash: 1e2d43f33a352d3f4502965c5368eb901e7bffdf
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="access-levels-in-visual-basic"></a>Níveis de acesso no Visual Basic
O *nível de acesso* de um elemento declarado é a extensão da habilidade de acessá-lo, ou seja, o que o código tem permissão para ler ou gravar nele. Isso é determinado não apenas por como você declarar o elemento em si, mas também pelo nível de acesso do contêiner do elemento. Código que não é possível acessar um elemento contendo não pode acessar qualquer um de seus elementos contidos, mesmo aqueles declaradas como `Public`. Por exemplo, um `Public` variável em um `Private` estrutura pode ser acessada de dentro da classe que contém a estrutura, mas não de fora dessa classe.  
  
## <a name="public"></a>Público  
 O [pública](../../../../visual-basic/language-reference/modifiers/public.md) palavra-chave na instrução de declaração especifica que o elemento pode ser acessado de código em qualquer lugar no mesmo projeto, de outros projetos que referenciem o projeto e de qualquer assembly criado a partir do projeto. O código a seguir mostra um exemplo `Public` declaração.  
  
```vb  
Public Class classForEverybody  
```  
  
 Você pode usar `Public` apenas no nível de namespace ou módulo. Isso significa que você pode declarar um elemento público no nível de um arquivo de origem ou o espaço para nome, ou dentro de uma interface, módulo, classe ou estrutura, mas não em um procedimento.  
  
## <a name="protected"></a>Protegido  
 O [protegidos](../../../../visual-basic/language-reference/modifiers/protected.md) palavra-chave na instrução de declaração especifica que o elemento pode ser acessado somente de dentro da mesma classe ou de uma classe derivada dessa classe. O código a seguir mostra um exemplo `Protected` declaração.  
  
```vb  
Protected Class classForMyHeirs  
```  
  
 Você pode usar `Protected` somente a classe nível e somente quando você declarar um membro de uma classe. Isso significa que você pode declarar um elemento protegido em uma classe, mas não no nível de um namespace ou arquivo de origem, ou dentro de uma interface, módulo, estrutura ou procedimento.  
  
## <a name="friend"></a>Friend  
 O [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) palavra-chave na instrução de declaração especifica que o elemento pode ser acessado de dentro do mesmo assembly, mas não de fora do assembly. O código a seguir mostra um exemplo `Friend` declaração.  
  
```vb  
Friend stringForThisProject As String  
```  
  
 Você pode usar `Friend` apenas no nível de namespace ou módulo. Isso significa que você pode declarar um elemento público no nível de um arquivo de origem ou o espaço para nome, ou dentro de uma interface, módulo, classe ou estrutura, mas não em um procedimento.  
  
## <a name="protected-friend"></a>Friend protegido  
 O `Protected` e `Friend` palavras-chave juntos na instrução de declaração especificam que o elemento pode ser acessado de classes derivadas ou dentro do mesmo assembly, ou ambos. O código a seguir mostra um exemplo `Protected Friend` declaração.  
  
```vb  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 Você pode usar `Protected Friend` somente a classe nível e somente quando você declarar um membro de uma classe. Isso significa que você pode declarar um elemento público em uma classe, mas não no nível de um namespace ou arquivo de origem, ou dentro de uma interface, módulo, estrutura ou procedimento.  
  
## <a name="private"></a>Particular  
 O [privada](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave na instrução de declaração especifica que o elemento pode ser acessado somente de dentro do mesmo módulo, classe ou estrutura. O código a seguir mostra um exemplo `Private` declaração.  
  
```vb  
Private numberForMeOnly As Integer  
```  
  
 Você pode usar `Private` apenas no nível de módulo. Isso significa que você pode declarar um elemento particular dentro de um módulo, classe ou estrutura, mas não no nível de um arquivo de origem ou namespace, dentro de uma interface ou em um procedimento.  
  
 No nível de módulo, o `Dim` instrução sem quaisquer palavras-chave de nível de acesso é equivalente a um `Private` declaração. No entanto, talvez você queira usar o `Private` palavra-chave para tornar o código mais fácil de ler e interpretar.  

## <a name="private-protected"></a>Privado protegido

O [privada protegida](../../../language-reference/modifiers/private-protected.md) palavra-chave na instrução de declaração especifica que o elemento pode ser acessado somente de dentro da mesma classe, bem como classes derivadas encontradas no mesmo assembly como a classe continente. O `Private Protected` modificador de acesso é suportado, começando com Visual Basic 15,5.

A exemplo a seguir mostra um `Private Protected` declaração:

```vb
Private Protected internalValue As Integer
```

Você pode declarar uma `Private Protected` elemento apenas dentro de uma classe. Você não pode declará-la em uma estrutura ou interface, nem você declará-la no nível de um arquivo de origem ou namespace, dentro de uma interface ou uma estrutura ou em um procedimento.

O `Private Protected` modificador de acesso é suportado pelo Visual Basic 15,5 e posteriores. Para usá-lo, você pode adicionar o elemento a seguir para o arquivo de projeto (*. vbproj) do Visual Basic. Como enquanto 15,5 do Visual Basic ou posterior está instalado em seu sistema, permite aproveitar todos os recursos de idioma com suporte pela versão mais recente do compilador do Visual Basic:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Para usar o `Private Protected` modificador de acesso, adicione o seguinte elemento ao seu arquivo de projeto (*. vbproj) do Visual Basic:

```xml
<PropertyGroup>
   <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

 ## <a name="access-modifiers"></a>Modificadores de acesso  
 As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*. A tabela a seguir compara os modificadores de acesso.  
  
|Modificador de acesso|Nível de acesso concedido|Elementos que você pode declarar com esse nível de acesso|Contexto de declaração dentro do qual você pode usar esse modificador|  
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|  
|`Public`|Irrestrito:<br /><br /> Qualquer código que pode ver um elemento público pode acessá-lo|Interfaces<br /><br /> Módulos<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Membros de estrutura<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Arquivo de origem<br /><br /> Namespace<br /><br /> Interface<br /><br /> Módulo<br /><br /> Classe<br /><br /> Estrutura|  
|`Protected`|Derivacionais:<br /><br /> A classe que declara um elemento protegido, ou uma classe derivada, pode acessar o elemento de código|Interfaces<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Classe|  
|`Friend`|Assembly:<br /><br /> O código no assembly que declara que um elemento de amigo pode acessá-lo|Interfaces<br /><br /> Módulos<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Membros de estrutura<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Arquivo de origem<br /><br /> Namespace<br /><br /> Interface<br /><br /> Módulo<br /><br /> Classe<br /><br /> Estrutura|  
|`Protected` `Friend`|União de `Protected` e `Friend`:<br /><br /> O código na mesma classe ou o mesmo assembly como um elemento amigo protegido, ou em qualquer classe derivada da classe do elemento, pode acessá-lo|Interfaces<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Classe|  
|`Private`|Contexto de declaração:<br /><br /> Código de tipo que declara um elemento particular, incluindo o código de tipos contidos, pode acessar o elemento|Interfaces<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Membros de estrutura<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Módulo<br /><br /> Classe<br /><br /> Estrutura|
|`Private Protected`|Código na classe que declara um elemento protegido particular, nem em uma classe derivada, localizada no mesmo assembly como a classe bas.|Interfaces<br /><br /> Classes<br /><br /> Estruturas<br /><br /> Procedimentos<br /><br /> Propriedades<br /><br /> Variáveis de membro<br /><br /> Constantes<br /><br /> Enumerações<br /><br /> Eventos<br /><br /> Declarações externas<br /><br /> Delegados|Classe|
  
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
