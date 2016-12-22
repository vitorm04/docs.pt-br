---
title: "Campos (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "campos [C#]"
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
caps.latest.revision: 29
caps.handback.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Campos (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A  *campo*  é uma variável de qualquer tipo que é declarado diretamente em um  [classe](../../../csharp/language-reference/keywords/class.md) ou  [struct](../../../csharp/language-reference/keywords/struct.md).  Os campos são  *membros* de seu tipo de recipiente.  
  
 Class ou struct pode ter campos de instância ou campos estáticos ou ambos.  Campos de instância são específicos a uma instância de um tipo.  Se você tiver uma classe de T, com um campo de instância F, você pode criar dois objetos do tipo t e modificar o valor de f em cada objeto sem afetar o valor do outro objeto.  Por outro lado, um campo estático pertence à própria classe e é compartilhado entre todas as instâncias dessa classe.  As alterações feitas de instância um irá ser visivelmente imediatamente a instâncias de b e c se eles acessarem o campo.  
  
 Geralmente, você deve usar campos somente para variáveis que têm acessibilidade particular ou protegida.  Os dados que sua classe expõe para o código do cliente devem ser fornecidos por meio de  [métodos](../../../fsharp/language-reference/members/methods.md),  [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md) e  [indexadores](../../../csharp/programming-guide/indexers/index.md).  Usando essas construções para acesso indireto a campos internos, você pode se proteger contra os valores de entrada inválidos.  Um campo privado que armazena os dados expostos por uma propriedade pública é chamado um  *armazenamento de backup* ou  *fazendo o campo*.  
  
 Normalmente, os campos armazenam os dados que devem ser acessados por mais de um método de classe e devem ser armazenados por mais tempo que o tempo de vida de qualquer método único.  Por exemplo, uma classe que representa uma data do calendário pode ter três campos de número inteiro: um para o mês, para o dia e outra para o ano.  Variáveis que não são usadas fora do escopo de um método único devem ser declaradas como  *variáveis locais* dentro do método body propriamente dito.  
  
 Campos são declarados no bloco de classe, especificando o nível de acesso do campo, seguido do tipo do campo, seguido do nome do campo.  Por exemplo:  
  
 [!code-cs[csProgGuideObjects#61](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_1.cs)]  
  
 Para acessar um campo em um objeto, adicione um período após o nome do objeto, seguido do nome do campo, como em `objectname.fieldname`.  Por exemplo:  
  
 [!code-cs[csProgGuideObjects#62](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_2.cs)]  
  
 Pode ser designado a um campo de um valor inicial usando o operador de atribuição quando o campo é declarado.  Para atribuir automaticamente o `day` campo para `"Monday"`, por exemplo, você poderia declarar `day` como no exemplo a seguir:  
  
 [!code-cs[csProgGuideObjects#63](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_3.cs)]  
  
 Campos sejam inicializados imediatamente antes que o construtor para a instância do objeto é chamado.  Se o construtor atribui o valor de um campo, ele substituirá qualquer valor fornecido durante a declaração de campo.  Para obter mais informações, consulte [Usando construtores](../../../csharp/programming-guide/classes-and-structs/using-constructors.md).  
  
> [!NOTE]
>  Um inicializador de campo não pode se referir a outros campos de instância.  
  
 Campos podem ser marcados como  [pública](../../../csharp/language-reference/keywords/public.md),  [particular](../../../csharp/language-reference/keywords/private.md),  [protegido](../../../csharp/language-reference/keywords/protected.md),  [interno](../../../csharp/language-reference/keywords/internal.md), ou `protected internal`.  Esses modificador de acessos definem como os usuários da classe podem acessar os campos.  Para obter mais informações, consulte [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Opcionalmente, pode ser declarado um campo  [estático](../../../csharp/language-reference/keywords/static.md).  Isso disponibiliza o campo para chamadores a qualquer hora, mesmo que nenhuma instância da classe existe.  Para obter mais informações, consulte [Classes static e membros de classes static](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Um campo pode ser declarado  [somente leitura](../../../csharp/language-reference/keywords/readonly.md).  Um campo somente leitura pode ser atribuído apenas um valor durante a inicialização ou em um construtor.  A `static``readonly` campo é muito semelhante a uma constante, exceto que o compilador C\# não tem acesso ao valor de um campo somente leitura estático em tempo de compilação, somente em tempo de execução.  Para obter mais informações, consulte [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md).  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Usando construtores](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)   
 [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md)   
 [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [Classes e membros de classes abstract e sealed](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)