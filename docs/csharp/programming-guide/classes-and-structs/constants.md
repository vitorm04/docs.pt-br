---
title: "Constantes (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "Linguagem C#, constantes"
  - "constantes [C#]"
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Constantes (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Constantes são imutáveis valores que são conhecidos no momento da compilação e não são alterados durante a vida útil do programa.  Constantes são declarados com o  [const](../../../csharp/language-reference/keywords/const.md) modificador.  Somente C\# tipos internos \(excluindo <xref:System.Object?displayProperty=fullName>\) podem ser declarados como `const`.  Para obter uma lista dos tipos internos, consulte [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md).  Tipos definidos pelo usuário, incluindo classes, structs e arrays, não podem ser `const`.  Use o  [somente leitura](../../../csharp/language-reference/keywords/readonly.md) não é possível alterar o modificador para criar uma classe, struct ou matriz é inicializada de uma vez no tempo de execução \(por exemplo, em um construtor\) e daí em diante.  
  
 C\# não oferece suporte a `const` métodos, propriedades ou eventos.  
  
 O tipo enum permite que você defina a constantes nomeadas para tipos internos integrais \(por exemplo `int`, `uint`, `long`e assim por diante\).  Para obter mais informações, consulte [enum](../../../csharp/language-reference/keywords/enum.md).  
  
 Constantes devem ser inicializadas conforme elas são declaradas.  Por exemplo:  
  
 [!code-cs[csProgGuideObjects#64](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_1.cs)]  
  
 Neste exemplo, a constante `months` é sempre 12 e não pode ser alterado até mesmo pela própria classe.  Na verdade, quando o compilador encontra um identificador constante no código\-fonte do C\# \(por exemplo, `months`\), ele substitui o valor literal diretamente para o código de linguagem intermediária \(IL\) que ele produz.  Porque não há nenhum endereço de variável associado a uma constante em tempo de execução, `const` campos não podem ser passados por referência e não pode aparecer como um valor de l em uma expressão.  
  
> [!NOTE]
>  Tenha cuidado ao fazer referência a valores constantes definidas em outros códigos como DLLs.  Se uma nova versão da DLL define um novo valor para a constante, o seu programa ainda mantenha o valor literal antigo até que ele é recompilado contra a nova versão.  
  
 Várias constantes do mesmo tipo podem ser declarados ao mesmo tempo, por exemplo:  
  
 [!code-cs[csProgGuideObjects#65](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_2.cs)]  
  
 A expressão que é usada para inicializar uma constante pode consultar outra constante se ele não cria uma referência circular.  Por exemplo:  
  
 [!code-cs[csProgGuideObjects#66](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_3.cs)]  
  
 Constantes podem ser marcados como  [pública](../../../csharp/language-reference/keywords/public.md),  [particular](../../../csharp/language-reference/keywords/private.md),  [protegido](../../../csharp/language-reference/keywords/protected.md),  [interno](../../../csharp/language-reference/keywords/internal.md), ou `protected``internal`.  Esses modificadores de acesso definem como os usuários da classe podem acessar a constante.  Para obter mais informações, consulte [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Constantes são acessados como se fossem  [estático](../../../csharp/language-reference/keywords/static.md) campos como o valor da constante é a mesma para todas as instâncias do tipo.  Você não usar o `static` palavra\-chave para declará\-los.  Expressões que não estão na classe que define a constante devem usar o nome da classe, um período e o nome da constante para acessar a constante.  Por exemplo:  
  
 [!code-cs[csProgGuideObjects#67](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_4.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Tipos](../../../visual-basic/reference/command-line-compiler/index.md)   
 [readonly](../../../csharp/language-reference/keywords/readonly.md)   
 [Imutabilidade na C\# Part One: tipos de imutabilidade](http://go.microsoft.com/fwlink/?LinkId=112379)