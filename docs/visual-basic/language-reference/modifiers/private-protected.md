---
title: Privado protegido (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 23fd6583182a1fee544d0458dc3fc390aed86b9f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="private-protected-visual-basic"></a>Privado protegido (Visual Basic)

O `Private Protected` combinação de palavra-chave é um modificador de acesso de membro. Um `Private Protected` membro é acessado por todos os membros em sua classe, bem como por tipos derivados da classe que contém, mas somente se forem encontrados em seu assembly que contém. 

Você pode especificar `Private Protected` somente em membros de classes; não é possível aplicar `Private Protected` para membros de uma estrutura como estruturas não podem ser herdadas.

O `Private Protected` modificador de acesso é suportado pelo Visual Basic 15,5 e posteriores. Para usá-lo, você pode adicionar o elemento a seguir para o arquivo de projeto (*. vbproj) do Visual Basic. Como enquanto 15,5 do Visual Basic ou posterior está instalado em seu sistema, permite aproveitar todos os recursos de idioma com suporte pela versão mais recente do compilador do Visual Basic:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> No Visual Studio, selecionando Ajuda F1 em `private protected` fornece ajuda para o [privada](private.md) ou [protegido](protected.md). O IDE adota o token único sob o cursor em vez da palavra composta.

## <a name="rules"></a>Regras

- **Contexto de declaração.** Você pode usar `Private Protected` somente no nível de classe. Isso significa que o contexto da declaração para um `Protected` elemento deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, módulo, estrutura ou procedimento.

## <a name="behavior"></a>Comportamento

- **Nível de acesso.** Todo o código em uma classe pode acessar seus elementos. O código em qualquer classe que deriva de uma classe base e está contido no mesmo assembly pode acessar todos os `Private Protected` elementos da classe base. No entanto, o código em qualquer classe que deriva de uma classe base e está contido em um assembly diferente não pode acessar a classe base `Private Protected` elementos.

- **Modificadores de acesso.** As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*. Para uma comparação entre os modificadores de acesso, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).
  
 O `Private Protected` modificador pode ser usado nesses contextos:  
  
 [Instrução class](../../../visual-basic/language-reference/statements/class-statement.md) de uma classe aninhada  
  
 [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Instrução delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) de um delegado aninhado em uma classe  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md) de um eumeration aninhados em uma classe 
  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução interface](../../../visual-basic/language-reference/statements/interface-statement.md) de uma interface aninhada em uma classe 
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Declaração de estrutura](../../../visual-basic/language-reference/statements/structure-statement.md) de uma estrutura aninhada em uma classe 
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também

[Público](../../../visual-basic/language-reference/modifiers/public.md)  
[Protegido](../../../visual-basic/language-reference/modifiers/protected.md)  
[Friend](friend.md)   
[Privado](../../../visual-basic/language-reference/modifiers/private.md)  
[Friend protegido](./protected-friend.md)   
[Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
