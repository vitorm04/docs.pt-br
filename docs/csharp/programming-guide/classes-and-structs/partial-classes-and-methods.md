---
title: "Classes e m&#233;todos partial (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "Linguagem C#, classes e métodos parciais"
  - "classes parciais [C#]"
  - "métodos parciais [C#]"
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
caps.latest.revision: 35
caps.handback.revision: 35
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Classes e m&#233;todos partial (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

É possível dividir a definição de um  [classe](../../../csharp/language-reference/keywords/class.md) ou um  [struct](../../../csharp/language-reference/keywords/struct.md), um  [interface](../../../csharp/language-reference/keywords/interface.md) ou um método ao longo de dois ou mais arquivos de origem.  Cada arquivo contém uma seção para definição de tipo ou método, e todas as partes são combinadas quando a aplicação é compilada.  
  
## Classes parciais  
 Existem várias situações em que dividir uma classe é desejável:  
  
-   Ao trabalhar em grandes projetos, dividir uma classe em arquivos separados permite múltiplos programadores a trabalhar sobre ela, ao mesmo tempo.  
  
-   Ao trabalhar com a fonte gerado automaticamente, código pode ser adicionado à classe sem ter que recriar o arquivo de origem.  Visual Studio usa esta abordagem quando ele cria o Windows Forms, código adptadores de Web Service, e assim sucessivamente.  Você pode criar o código que usa essas classes sem ter que modificar o arquivo criado pelo Visual Studio.  
  
-   Para dividir uma definição de classe, use o  [parcial](../../../csharp/language-reference/keywords/partial-type.md) modificador de palavra\-chave, como mostrado aqui:  
  
 [!code-cs[csProgGuideObjects#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_1.cs)]  
  
 O `partial` palavra\-chave indica que outras partes da classe, struct, ou interface pode ser definido no namespace.  Todas as partes devem usar o `partial` palavra\-chave.  Todas as partes devem estar disponíveis em tempo de compilação para formar o tipo final.  Todas as partes devem ter a mesma acessibilidade, como `public`, `private`e assim por diante.  
  
 Se qualquer parte é declarado como abstrato, o tipo inteiro é considerado abstrato.  Se qualquer parte for declarada lacrado, o tipo inteiro será considerada lacrados.  Se qualquer parte declara um tipo base, o tipo inteiro herda dessa classe.  
  
 Todas as partes que especificar uma classe base devem concordar, mas partes omitir uma classe base ainda herdam o tipo base.  Partes podem especificar diferentes interfaces de base e o tipo final implementa todas as interfaces listadas por todas as declarações de parciais.  Qualquer classe, struct ou membros de interface declarados em uma definição parcial estão disponíveis para todas as outras partes.  O tipo final é a combinação de todas as partes em tempo de compilação.  
  
> [!NOTE]
>  O `partial` modificador não está disponível em declarações delegate ou enumeração.  
  
 O exemplo a seguir mostra que tipos aninhados podem ser parciais, mesmo se o tipo que são aninhados não é parcial propriamente dito.  
  
 [!code-cs[csProgGuideObjects#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_2.cs)]  
  
 Em tempo de compilação, os atributos das definições de tipo parcial são mesclados.  Por exemplo, considere as seguintes declarações:  
  
 [!code-cs[csProgGuideObjects#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_3.cs)]  
  
 Eles são equivalentes para as seguintes declarações:  
  
 [!code-cs[csProgGuideObjects#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_4.cs)]  
  
 A seguir é mesclada de todas as definições de tipo parcial:  
  
-   Comentários XML  
  
-   interfaces  
  
-   atributos de parâmetro de tipo genérico  
  
-   atributos de classe  
  
-   membros  
  
 Por exemplo, considere as seguintes declarações:  
  
 [!code-cs[csProgGuideObjects#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_5.cs)]  
  
 Eles são equivalentes para as seguintes declarações:  
  
 [!code-cs[csProgGuideObjects#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_6.cs)]  
  
### Restrições  
 Existem várias regras a seguir quando você estiver trabalhando com definições de classe parcial:  
  
-   Todas as definições de tipo parcial deve ser partes do mesmo tipo devem ser modificadas com `partial`.  Por exemplo, as seguintes declarações de classe geram um erro:  
  
     [!code-cs[csProgGuideObjects#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_7.cs)]  
  
-   O `partial` modificador só pode aparecer imediatamente antes das palavras\-chave `class`, `struct`, ou `interface`.  
  
-   Aninhadas tipos parciais são permitidos em definições de tipo parcial, conforme ilustrado no exemplo a seguir:  
  
     [!code-cs[csProgGuideObjects#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_8.cs)]  
  
-   Todas as definições de tipo parcial deve ser partes do mesmo tipo devem ser definidas no mesmo assembly e o mesmo módulo \(arquivo. exe ou. dll\).  Definições parciais não podem se estender por vários módulos.  
  
-   O nome da classe e os parâmetros de tipo genérico devem coincidir com todas as definições de tipo parcial.  Tipos genéricos podem ser parciais.  Cada declaração parcial deve usar os mesmos nomes de parâmetro na mesma ordem.  
  
-   As seguintes palavras\-chave em uma definição de tipo parcial são opcionais, mas se estiver presente em uma definição de tipo parcial, não é possível entrar em conflito com as palavras\-chave especificadas na outra definição parcial para o mesmo tipo:  
  
    -   [Público](../../../csharp/language-reference/keywords/public.md)  
  
    -   [Particular](../../../csharp/language-reference/keywords/private.md)  
  
    -   [Protegido](../../../csharp/language-reference/keywords/protected.md)  
  
    -   [interno](../../../csharp/language-reference/keywords/internal.md)  
  
    -   [abstrata](../../../csharp/language-reference/keywords/abstract.md)  
  
    -   [autenticada](../../../csharp/language-reference/keywords/sealed.md)  
  
    -   classe base  
  
    -   [nova](../../../csharp/language-reference/keywords/new.md) modificador \(partes aninhadas\)  
  
    -   restrições genéricas  
  
         Para obter mais informações, consulte [Restrições a parâmetros de tipo](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).  
  
## Exemplo 1  
  
### Descrição  
 No exemplo a seguir, os campos e o construtor da classe, `CoOrds`, são declarados em uma definição de classe parcial e o membro, `PrintCoOrds`, é declarado em outra definição de classe parcial.  
  
### Código  
 [!code-cs[csProgGuideObjects#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_9.cs)]  
  
## Exemplo 2  
  
### Descrição  
 O exemplo a seguir mostra que você também pode desenvolver interfaces e structs parcial.  
  
### Código  
 [!code-cs[csProgGuideObjects#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_10.cs)]  
  
## Métodos Parciais  
 Uma classe ou um struct parcial pode conter um método também parcial.  Uma parte da classe contém a assinatura do método.  Uma implementação opcional pode ser definida na mesma parte ou outra parte.  Se a implementação não for fornecida, em seguida, o método e todas as chamadas ao método serão removidas em tempo de compilação.  
  
 Métodos parciais permitem que o implementador de uma parte de uma classe definir um método semelhante a um evento.  O implementador da outra parte da classe pode decidir se deseja implementar o método ou não.  Se o método não é implementado, o compilador remove o método de assinatura e todas as chamadas ao método.  As chamadas para o método, incluindo qualquer resultado que ocorreria da avaliação de argumentos nas chamadas, não têm efeito em tempo de execução.  Portanto, qualquer código na classe parcial livremente pode usar um método parcial, mesmo que a implementação não for fornecida.  Nenhum erro de tempo de compilação ou runtime resultará se o método for chamado, mas não implementado.  
  
 Métodos parciais são especialmente úteis como uma forma de personalizar o código gerado.  Eles permitem que um nome de método e a assinatura a ser reservado, para que o código gerado pode chamar o método, mas o desenvolvedor pode decidir se deseja implementar o método.  Bem como classes parciais, os métodos parciais permitem código criado por um gerador de código e o código criado por um desenvolvedor humano trabalhem em conjunto, sem custos de tempo de execução.  
  
 Uma declaração de método parcial consiste em duas partes: a definição e a implementação.  Esses podem ser em partes separadas de uma classe parcial ou na mesma parte.  Se não houver nenhuma declaração de implementação, o compilador otimiza distância tanto a definição de declaração e todas as chamadas ao método.  
  
```  
// Definition in file1.cs  
partial void onNameChanged();  
  
// Implementation in file2.cs  
partial void onNameChanged()  
{  
  // method body  
}  
```  
  
-   Declarações de métodos parciais devem começar com a palavra\-chave contextual  [parcial](../../../csharp/language-reference/keywords/partial-type.md) e o método deve retornar  [void](../../../csharp/language-reference/keywords/void.md).  
  
-   Os métodos parciais podem ter  [ref](../../../csharp/language-reference/keywords/ref.md) , mas não  [check\-out](../../../csharp/language-reference/keywords/out.md) parâmetros.  
  
-   Métodos parciais são implicitamente  [particular](../../../csharp/language-reference/keywords/private.md), e portanto não pode ser  [virtual](../../../csharp/language-reference/keywords/virtual.md).  
  
-   Métodos parciais não podem ser  [extern](../../../csharp/language-reference/keywords/extern.md), porque a presença do corpo determina se eles estão definindo ou implementação.  
  
-   Os métodos parciais podem ter  [estático](../../../csharp/language-reference/keywords/static.md) e  [não seguros](../../../csharp/language-reference/keywords/unsafe.md) modificadores.  
  
-   Métodos parciais podem ser genéricos.  As restrições são colocadas na declaração de método parcial a definição e, opcionalmente, podem ser repetidas na implementação.  Nomes de parâmetro e tipo de parâmetro não tem o mesmo na declaração de implementação, como naquela definição.  
  
-   Você pode fazer uma  [delegar](../../../csharp/language-reference/keywords/delegate.md) um método parcial que foi definido e implementado, mas não um método parcial que só foi definido.  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)   
 [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md)   
 [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md)   
 [partial \(tipo\)](../../../csharp/language-reference/keywords/partial-type.md)