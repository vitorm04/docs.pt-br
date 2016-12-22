---
title: "Tipo de dados Object | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Object"
  - "vb.Variant"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "tipos de dados [Visual Basic], atribuindo"
  - "tipo de dados Object"
  - "tipo de dados Object, referência"
  - "variáveis de objeto, Tipo de objeto"
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de dados Object
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Mantém endereços de que se referem a objetos.  Você pode atribuir qualquer tipo de referência \(cadeia de caracteres, array, classe ou Interface\) para uma variável `Object`.  Uma variável `Object` também pode se referir aos dados de qualquer tipo de valor \(numérico, `Boolean`, `Char`,`Date`,estrutura, ou enumeração\).  
  
## Comentários  
 O tipo de dados `Object` pode apontar para dados de qualquer tipo de dados, incluindo qualquer instância do objeto que aplicativo reconhece.  Use `Object` quando você não souber em tempo de compilação para qual tipo de dados a variável pode apontar.  
  
 O valor padrão do `Object` é `Nothing` \(uma referência nula\).  
  
## Tipos de dados  
 Você pode atribuir uma variável, constante ou expressão de qualquer tipo de dados a uma variável `Object`.  Para determinar o tipo de dados a que uma variável `Object` atualmente refere\-se, você pode usar o método <xref:System.Type.GetTypeCode%2A> da classe <xref:System.Type?displayProperty=fullName>.  O exemplo a seguir ilustra isto:  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 O  tipo de dados `Object` é um tipo de referência.  No entanto, o Visual Basic trata uma variável `Object` como um tipo de valor quando ela se refere a dados de um tipo de dados de valor.  
  
## Armazenamento  
 Para qualquer tipo de dados ao qual ela se refere, uma variável `Object`não contém o valor dos dados em si, mas em vez disso, um ponteiro para o valor.  Ela sempre usa quatro bytes na memória do computador, mas isso não inclui o armazenamento de dados que representam o valor da variável.  Por causa do código que usa o ponteiro para localizar os dados, variáveis `Object` armazenando os tipos de valor são um pouco mais lentas para acesso do que variáveis tipadas explicitamente.  
  
## Dicas de Programação  
  
-   **Considerações de Interoperabilidade.** Se você estiver interfaceando com componentes não escritos para o.NET Framework, por exemplo automação ou objetos COM, tenha em mente que o ponteiro em outros ambientes não é compatível com o tipo do Visual Basic `Object` .  
  
-   **Desempenho.** Uma variável que você declara com o tipo de `Object` é flexível o suficiente para conter uma referência a qualquer objeto.  No entanto, quando você chama um método ou propriedade nesse tipo de variável, você sempre provoca *associação tardia*  \(no tempo de execução\).  Para forçar  *associação inicial*  \(em tempo de compilação\) e um melhor desempenho, declarar a variável com um nome de classe específico, ou converta\-o para o tipo de dados específico.  
  
     Quando você declarar uma variável de objeto, tente usar um tipo de classe específico, por exemplo <xref:System.OperatingSystem>, em vez do tipo generalizado `Object`.  Você também deve usar a classe mais específica disponível, tais como <xref:System.Windows.Forms.TextBox> em vez de <xref:System.Windows.Forms.Control>, para que você possa acessar suas propriedades e métodos.  Geralmente, você pode usar a lista **Classes** no **pesquisador de objetos** para localizar nomes de classe disponíveis.  
  
-   **Ampliação.** Todos os tipos de dados e todos os tipos de referência alargam a `Object` o tipo de dados.  Isso significa que você pode converter qualquer tipo para `Object` sem encontrar um erro <xref:System.OverflowException?displayProperty=fullName>.  
  
     No entanto, se você converter entre tipos de valor e `Object`, o Visual Basic executa operações chamadas *boxing* e  *unboxing* , que tornam a execução mais lenta.  
  
-   **Caracteres de tipo.** `Object` não tem caracteres de tipo literais ou caracteres de tipo identificadores.  
  
-   **Tipo de Framework.** O tipo correspondente no.NET Framework é a classe de <xref:System.Object?displayProperty=fullName> .  
  
## Exemplo  
 O exemplo a seguir ilustra uma variável `Object` apontando para uma instância do objeto.  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## Consulte também  
 <xref:System.Object>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Como determinar se dois objetos estão relacionados](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)   
 [Como determinar se dois objetos são idênticos](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)