---
title: "Controle de vers&#227;o com as palavras-chave override e new (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "Linguagem C#, override e new"
  - "Linguagem C#, controle de versão"
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Controle de vers&#227;o com as palavras-chave override e new (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Destina\-se a linguagem C\# para que o controle de versão entre  [base](../../../csharp/language-reference/keywords/base.md) e classes derivadas em bibliotecas diferentes podem evoluir e manter a compatibilidade com versões anteriores.  Isso significa, por exemplo, que a introdução de um novo membro em uma base de  [classe](../../../csharp/language-reference/keywords/class.md) com o mesmo nome como um membro em uma classe de derivada é completamente suportado por C\# e não resultar em comportamento inesperado.  Isso também significa que uma classe deve declarar explicitamente se um método é intencional para substituir um métodode herdado, ou se um método é um novo método que oculta um nome semelhante métodoherdado.  
  
 No C\#, classes derivadas podem conter métodos com o mesmo nome como métodos de classe base .  
  
-   Ométodo do classe basedeve ser definido  [virtual](../../../csharp/language-reference/keywords/virtual.md).  
  
-   Se o método na classe derivada não for precedido por  [nova](../../../csharp/language-reference/keywords/new.md) ou  [substituir](../../../csharp/language-reference/keywords/override.md) palavras\-chave, o compilador emitirá um aviso e o método se comportará como se a `new` palavra\-chave estavam presentes.  
  
-   Se o método na classe derivada é precedido de `new` palavra\-chave, o método é definido como sendo independente do método na classe base.  
  
-   Se o método na classe derivada é precedido de `override` palavra\-chave, objetos derivados da classe irá chamar esse método em vez dométodode classe base.  
  
-   Ométodo de classe basepode ser chamados de dentro da classe de derivada usando o `base` palavra\-chave.  
  
-   O `override`, `virtual`, e `new` palavras\-chave também podem ser aplicadas a propriedades, indexadores e eventos.  
  
 Por padrão, o C\# métodos não são virtuais.  Se um método é declarado como virtual, qualquer classe que herda o método pode implementar sua própria versão.  Para tornar um método virtual, o `virtual` modificador é usado nadeclaração do métododa classe base.   A classe derivada pode, em seguida, substituir o método de virtual base usando o `override` palavra\-chave ou ocultar o método virtual na classe base usando o `new` palavra\-chave.    Caso nem o `override` palavra\-chave , nem o `new` palavra\-chave for especificado, o compilador emitirá um aviso e o método na classe derivada será ocultar o método na classe base.  
  
 Para demonstrar isso na prática, assumir por um momento que a empresa criou uma classe chamada `GraphicsClass`, que usa o seu programa .  Veja a seguir `GraphicsClass`:  
  
 [!code-cs[csProgGuideInheritance#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_1.cs)]  
  
 Sua empresa usa essa classee usá\-lo para derivar sua própria classe, adicionando um novo método:  
  
 [!code-cs[csProgGuideInheritance#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_2.cs)]  
  
 Seu aplicativo é usado sem problemas, até que a empresa a lança uma nova versão do `GraphicsClass`, que se parece com o código a seguir:  
  
 [!code-cs[csProgGuideInheritance#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_3.cs)]  
  
 A nova versão do `GraphicsClass` agora contém um método chamado `DrawRectangle`.  Inicialmente, nada ocorre.  A nova versão ainda é binário compatível com a antiga versão.  Qualquer software que você implantou continue a funcionar, mesmo se a nova classe estiver instalado nesses sistemas de computador.  As chamadas existentes para o método `DrawRectangle` continuarão a fazer referência a sua versão, na classederivada.  
  
 No entanto, assim você recompilar seu aplicativo usando a nova versão do `GraphicsClass`, você receberá um aviso do compilador, CS0108.  Este aviso informa que você deve considerar como você deseja que seu `DrawRectangle` método para se comportar em seu aplicativo.  
  
 Se você quiser que seu método para substituir o novométodode classe base, use o `override` palavra\-chave:  
  
 [!code-cs[csProgGuideInheritance#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_4.cs)]  
  
 O `override` palavra\-chave certifica\-se de que qualquer objeto derivado de `YourDerivedGraphicsClass` usará a classede derivadaversão do `DrawRectangle`.    Objetos derivados de `YourDerivedGraphicsClass` ainda pode acessar aversão de classe basedo `DrawRectangle` usando a palavra\-chavede base:  
  
 [!code-cs[csProgGuideInheritance#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_5.cs)]  
  
 Se você não quiser que seu método para substituir o novo classe base método, as considerações seguintes aplicar.  Para evitar confusão entre os dois métodos, você pode renomear o seu método.  Isso pode ser demorado e erro\-propenso a erros e simplesmente não é prático em alguns casos.  No entanto, se o seu projeto é relativamente pequena, você pode usar do Visual Studioopções de refatoração para renomear o método.  Para mais informações, consulte [Refatorando classes e tipos \(Designer de Classe\)](/visual-studio/ide/refactoring-classes-and-types-class-designer).  
  
 Como alternativa, você pode evitar que o aviso usando a palavra\-chave `new` em sua definição de derivada classe :  
  
 [!code-cs[csProgGuideInheritance#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_6.cs)]  
  
 Usando o `new` palavra\-chave , que informa o compilador que sua definição oculta a definição que está contida na classe base.   Este é o comportamento padrão.  
  
## Seleção de método e substituição  
 Quando um método é chamado em uma classe, o C\# compilador seleciona o melhor método para chamar se mais de um método é compatível com a chamada, como quando há dois métodos com o mesmo nome e parâmetros que são compatíveis com o parâmetro passado.  Os métodos a seguir seria compatíveis:  
  
 [!code-cs[csProgGuideInheritance#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_7.cs)]  
  
 Quando `DoWork` é chamado em uma instância de `Derived`, C\# compilador tentará primeiro fazer a chamada compatível com as versões do `DoWork` originalmente declarado em `Derived`.  Métodos de substituição não são considerados como declarado em uma classe, são novas implementações de um método declarado em uma classe base.  Somente se o C\# compilador não pode corresponder a chamada do método a um método de original em `Derived` ele tentará coincidir com a chamada para um método com o mesmo nome e parâmetros compatíveis.  Por exemplo:  
  
 [!code-cs[csProgGuideInheritance#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_8.cs)]  
  
 Porque a variável `val` pode ser convertido em um double implicitamente, as chamadas de compilador C\# `DoWork(double)` em vez de `DoWork(int)`.   Há duas maneiras de evitar que isso aconteça.  Em primeiro lugar, evite a declaração de novos métodos com o mesmo nome de métodos virtuais.  Em segundo lugar, você pode instruir o C\# compilador para chamar o método virtual, tornando a pesquisar a lista demétodo de classe basepor Projetando uma instância do `Derived` para `Base`.   Porque o método é virtual, a implementação de `DoWork(int)` na `Derived` será chamado.  Por exemplo:  
  
 [!code-cs[csProgGuideInheritance#34](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_9.cs)]  
  
 Para obter mais exemplos de `new` e `override`, consulte [Quando usar as palavras\-chave override e new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Métodos](../../../fsharp/language-reference/members/methods.md)   
 [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md)