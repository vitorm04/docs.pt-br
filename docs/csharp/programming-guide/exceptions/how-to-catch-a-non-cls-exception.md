---
title: "Como capturar uma exceção não CLS | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
caps.latest.revision: 8
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
ms.openlocfilehash: 3515ecab379a0e910cdd5ba82a4a39b085cc816f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-catch-a-non-cls-exception"></a>Como capturar uma exceção não compatível com CLS
Algumas linguagens .NET, incluindo o C++/CLI, permite que os objetos lancem exceções que não derivam de <xref:System.Exception>. Essas exceções são chamadas de *exceções não CLS* ou *não exceções*. No [!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)] não é possível lançar exceções não CLS, mas você pode capturá-las de duas maneiras:  
  
-   Dentro de um bloco `catch (Exception e)` como uma <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.  
  
     Por padrão, um assembly do [!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)] captura exceções não CLS como exceções encapsuladas. Use este método se você precisar de acesso à exceção original, que pode ser acessada por meio da propriedade <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A>. O procedimento, mais adiante neste tópico, explica como capturar exceções dessa maneira.  
  
-   Dentro de um bloco catch geral (um bloco catch sem um tipo de exceção especificado), que é colocado após um bloco `catch (Exception)` ou `catch (Exception e)`.  
  
     Use esse método quando desejar realizar alguma ação (como gravar em um arquivo de log) em resposta a exceções não CLS e você não precisa de acesso às informações de exceção. Por padrão, o Common Language Runtime encapsula todas as exceções. Para desabilitar esse comportamento, adicione esse atributo de nível de assembly em seu código, geralmente no arquivo AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.  
  
### <a name="to-catch-a-non-cls-exception"></a>Para capturar uma exceção não CLS  
  
1.  Dentro de um `catch(Exception e) block`, use a palavra-chave `as` para testar se `e` pode ser convertido em uma <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.  
  
2.  Acesse a exceção original por meio da propriedade <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como capturar uma exceção não CLS que foi lançada de uma biblioteca de classes escrita no C++ /CLR. Observe que, neste exemplo, o código cliente do [!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)] sabe com antecedência que o tipo de exceção que está sendo lançado é uma <xref:System.String?displayProperty=fullName>. Você pode converter a propriedade <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> de volta para o seu tipo original, desde que o tipo esteja acessível em seu código.  
  
```  
// Class library written in C++/CLR.  
   ThrowNonCLS.Class1 myClass = new ThrowNonCLS.Class1();  
  
   try  
   {  
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();   
   }  
  
   catch (Exception e)  
   {  
    RuntimeWrappedException rwe = e as RuntimeWrappedException;  
    if (rwe != null)      
    {  
      String s = rwe.WrappedException as String;  
      if (s != null)  
      {  
        Console.WriteLine(s);  
      }  
    }  
    else  
    {  
       // Handle other System.Exception types.  
    }  
   }             
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>   
 [Exceções e manipulação de exceções](../../../csharp/programming-guide/exceptions/index.md)
