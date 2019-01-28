---
title: Reflexão (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 8cdfe00a09d340d8b77f1f5582a3a3ad82c496b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537641"
---
# <a name="reflection-c"></a>Reflexão (C#)
A reflexão fornece objetos (do tipo <xref:System.Type>) que descrevem assemblies, módulos e tipos. É possível usar a reflexão para criar dinamicamente uma instância de um tipo, associar o tipo a um objeto existente ou obter o tipo de um objeto existente e invocar seus métodos ou acessar suas propriedades e campos. Se você estiver usando atributos em seu código, a reflexão permite acessá-los. Para obter mais informações, consulte [Atributos](../../../../docs/standard/attributes/index.md).  
  
 Veja um exemplo simples de reflexão usando o método estático `GetType` – herdado por todos os tipos da classe base `Object` – para obter o tipo de uma variável:  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 A saída é:  
  
 `System.Int32`  
  
 O exemplo a seguir usa a reflexão para obter o nome completo do assembly carregado.  
  
```csharp  
// Using Reflection to get information from an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 A saída é:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  As palavras-chave de C# `protected` e `internal` não têm significado no IL e não são usadas nas APIs de reflexão. Os termos correspondentes na IL são *Família* e *Assembly*. Para identificar um método `internal` usando a reflexão, use a propriedade <xref:System.Reflection.MethodBase.IsAssembly%2A>. Para identificar um método `protected internal`, use o <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.  
  
## <a name="reflection-overview"></a>Visão geral da reflexão  
 A reflexão é útil nas seguintes situações:  
  
-   Quando você precisa acessar atributos nos metadados do seu programa. Para obter mais informações, consulte [Recuperando informações armazenadas em atributos](../../../standard/attributes/retrieving-information-stored-in-attributes.md).  
  
-   Para examinar e instanciar tipos em um assembly.  
  
-   Para criar novos tipos em tempo de execução. Usar as classes em <xref:System.Reflection.Emit>.  
  
-   Para executar a associação tardia, acessar métodos em tipos criados em tempo de execução. Consulte o tópico [Carregando e usando tipos dinamicamente](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
## <a name="related-sections"></a>Seções relacionadas  
 Para saber mais:  
  
-   [Reflexão](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [Exibindo informações de tipo](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [Reflexão e tipos genéricos](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [Recuperando informações armazenadas em atributos](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Assemblies no Common Language Runtime](../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
