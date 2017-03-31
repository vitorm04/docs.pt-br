---
title: "Modificadores de acesso (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
caps.latest.revision: 32
author: BillWagner
ms.author: wiwagn
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9940012829038f585ad78a10b70fe2941753e40e
ms.lasthandoff: 03/13/2017

---
# <a name="access-modifiers-c-programming-guide"></a>Modificadores de acesso (Guia de Programação em C#)
Todos os tipos e membros de tipo têm um nível de acessibilidade, que controla se podem ser usados de outro código no seu assembly ou outros assemblies. Você pode usar os modificadores de acesso a seguir para especificar a acessibilidade de um tipo ou membro quando você o declarar:  
  
 [public](../../../csharp/language-reference/keywords/public.md)  
 O tipo ou membro pode ser acessado por qualquer outro código no mesmo assembly ou em outro assembly que faz referência a ele.  
  
 [private](../../../csharp/language-reference/keywords/private.md)  
 O tipo ou membro pode ser acessado somente pelo código na mesma classe ou struct.  
  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 O tipo ou membro pode ser acessado somente pelo código na mesma classe ou struct ou em uma classe derivada dessa classe.  
  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 O tipo ou membro pode ser acessado por qualquer código no mesmo assembly, mas não de outro assembly.  
  
 `protected internal`  
 O tipo ou membro pode ser acessado por qualquer código no assembly no qual ele é declarado ou de uma classe derivada em outro assembly. O acesso de outro assembly deve ocorrer dentro de uma declaração de classe que deriva da classe na qual o elemento interno protegido é declarado e deve ser executado por meio de uma instância do tipo de classe derivada.  
  
 Os exemplos a seguir demonstram como especificar modificadores de acesso em um tipo e membro:  
  
 [!code-cs[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_1.cs)]  
  
 Nem todos os modificadores de acesso podem ser usados por todos os tipos ou membros em todos os contextos e, em alguns casos, a acessibilidade de um membro de tipo é restrita pela acessibilidade do seu tipo recipiente. As seções a seguir fornecem mais detalhes sobre a acessibilidade.  
  
## <a name="class-and-struct-accessibility"></a>Acessibilidade de classe e struct  
 As classes e structs que são declarados dentro de um namespace (em outras palavras, que não estão aninhadas dentro de outras classes ou structs) podem ser públicos ou internos. Interno é o padrão se nenhum modificador de acesso for especificado.  
  
 Membros de struct, incluindo classes e structs aninhados, podem ser declarados como públicos, internos ou privados. Membros de classe, incluindo classes e structs aninhados, podem públicos, internos protegidos, protegidos, internos ou privados. O nível de acesso para membros de classes e membros de struct, incluindo classes e structs aninhados, é privado por padrão. Tipos aninhados privados não são acessíveis de fora do tipo recipiente.  
  
 Classes derivadas não podem ter acessibilidade maior do que seus tipos base. Em outras palavras, você não pode ter uma classe pública `B` que deriva de uma classe interna `A`. Se isso fosse permitido, teria o efeito de tornar `A` público, pois todos os membros internos ou protegidos de `A` são acessíveis da classe derivada.  
  
 Você pode permitir que outros assemblies específicos acessem seus tipos internos usando o InternalsVisibleToAttribute. Para obter mais informações, consulte [Assemblies amigáveis](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).  
  
## <a name="class-and-struct-member-accessibility"></a>Acessibilidade de membro de classe e struct  
 Membros de classe (incluindo structs e classes aninhados) podem ser declarados com qualquer um dos cinco tipos de acesso. Membros de struct não podem ser declarados como protegidos porque os structs não têm suporte à herança.  
  
 Normalmente, a acessibilidade de um membro não é maior que a acessibilidade do tipo que o contém. No entanto, um membro público de uma classe interna pode ser acessível de fora do assembly se o membro implementa os métodos de interface ou substitui os métodos virtuais que são definidos em uma classe base pública.  
  
 O tipo de qualquer membro que seja um campo, propriedade ou evento deve ser pelo menos tão acessível quanto o próprio membro. Da mesma forma, o tipo de retorno e os tipos de parâmetro de qualquer membro que é um método, indexador ou delegado devem ser pelo menos tão acessíveis quanto o próprio membro. Por exemplo, você não pode ter um método público `M` que retorna uma classe `C`, a menos que `C` também seja público. Da mesma forma, você não pode ter uma propriedade protegida do tipo `A` se `A` for declarado como particular.  
  
 Os operadores definidos pelo usuário sempre devem ser declarados como públicos. Para obter mais informações, consulte [operador (Referência de C#)](../../../csharp/language-reference/keywords/operator.md).  
  
 Destruidores não podem ter modificadores de acessibilidade.  
  
 Para definir o nível de acesso para um membro de classe ou de struct, adicione a palavra-chave apropriada à declaração do membro, como mostrado o exemplo a seguir.  
  
 [!code-cs[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_2.cs)]  
  
> [!NOTE]
>  O nível de acessibilidade interno protegido significa protegido OU interno, não protegido E interno. Em outras palavras, um membro interno protegido pode ser acessado de qualquer classe no mesmo assembly, incluindo as classes derivadas. Para limitar a acessibilidade para apenas classes derivadas no mesmo assembly, declare a classe em si como interna e declare seus membros como protegidos.  
  
## <a name="other-types"></a>Outros tipos  
 Interfaces declaradas diretamente dentro de um namespace podem ser declaradas como públicas ou internas e, exatamente como as classes e structs, as interfaces assumem como padrão o acesso interno. Membros de interface sempre são públicos, pois a finalidade de uma interface é permitir que outros tipos acessem uma classe ou struct. Nenhum modificador de acesso pode ser aplicado aos membros de interface.  
  
 Membros de enumeração sempre são públicos e nenhum modificador de acesso pode ser aplicado.  
  
 Delegados se comportam como classes e structs. Por padrão, eles têm acesso interno quando declarados diretamente dentro de um namespace e acesso privado quando aninhados.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [class](../../../csharp/language-reference/keywords/class.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)   
 [interface](../../../csharp/language-reference/keywords/interface.md)
