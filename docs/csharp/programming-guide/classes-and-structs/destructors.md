---
title: "Finalizadores (Guia de Programação em C#)"
ms.date: 2017-05-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
caps.latest.revision: 24
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 43bb7e6488da5eda863e7ad70b25c9bf55bebb52
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="finalizers-c-programming-guide"></a>Finalizadores (Guia de Programação em C#)
Finalizadores são usados para destruir instâncias de classes.  
  
## <a name="remarks"></a>Comentários  
  
-   Os finalizadores não podem ser definidos em structs. Eles são usados somente com classes.  
  
-   Uma classe pode ter somente um finalizador.  
  
-   Os finalizadores não podem ser herdados ou sobrecarregados.  
  
-   Os finalizadores não podem ser chamados. Eles são invocados automaticamente.  
  
-   Um finalizador não usa modificadores ou não tem parâmetros.  
  
 Por exemplo, o seguinte é uma declaração de um finalizador para a classe `Car`.
  
 [!code-cs[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_1.cs)]  

Um finalizador também pode ser implementado como uma definição do corpo da expressão, como mostra o exemplo a seguir.

[!code-cs[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 O finalizador chama implicitamente <xref:System.Object.Finalize%2A> na classe base do objeto. Portanto, uma chamada para um finalizador é convertida implicitamente para o código a seguir:  
  
```csharp  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 Isso significa que o método `Finalize` é chamado de forma recursiva para todas as instâncias da cadeia de herança, da mais derivada à menos derivada.  
  
> [!NOTE]
>  Finalizadores vazios não devem ser usados. Quando uma classe contém um finalizador, uma entrada é criada na fila `Finalize`. Quando o finalizador é chamado, o coletor de lixo é invocado para processar a fila. Um finalizador vazio apenas resulta na perda de desempenho desnecessária.  
  
 O programador não tem controle sobre quando o finalizador é chamado porque isso é determinado pelo coletor de lixo. O coletor de lixo procura objetos que não estão mais sendo usados pelo aplicativo. Se considerar um objeto qualificado para finalização, ele chamará o finalizador (se houver) e recuperará a memória usada para armazenar o objeto. Os finalizadores também são chamados quando o programa é encerrado.  
  
 É possível forçar a coleta de lixo chamando <xref:System.GC.Collect%2A>, mas na maioria das vezes, isso deve ser evitado porque pode criar problemas de desempenho.  
  
## <a name="using-finalizers-to-release-resources"></a>Usando finalizadores para liberar recursos  
 Em geral, o C# não demanda tanto gerenciamento de memória quanto é necessário quando você desenvolve usando uma linguagem que não tem como destino um tempo de execução com coleta de lixo. Isso ocorre porque o coletor de lixo do .NET Framework gerencia implicitamente a alocação e a liberação de memória para seus objetos. No entanto, quando seu aplicativo encapsula recursos não gerenciados, como janelas, arquivos e conexões de rede, você deve usar finalizadores para liberar esses recursos. Quando o objeto está qualificado para finalização, o coletor de lixo executa o método `Finalize` do objeto.  
  
## <a name="explicit-release-of-resources"></a>Liberação explícita de recursos  
 Se seu aplicativo estiver usando um recurso externo caro, também será recomendável fornecer uma maneira de liberar explicitamente o recurso antes que o coletor de lixo libere o objeto. Você faz isso implementando um método `Dispose` da interface <xref:System.IDisposable> que executa a limpeza necessária para o objeto. Isso pode melhorar consideravelmente o desempenho do aplicativo. Mesmo com esse controle explícito sobre os recursos, o finalizador se tornará uma proteção usada para limpar os recursos se a chamada para o método `Dispose` falhar.  
  
 Para obter mais detalhes sobre limpeza de recursos, consulte os seguintes tópicos:  
  
-   [Limpando recursos não gerenciados](../../../standard/garbage-collection/unmanaged.md)  
  
-   [Implementando um método dispose](../../../standard/garbage-collection/implementing-dispose.md)  
  
-   [Instrução using](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria três classes que compõem uma cadeia de herança. A classe `First` é a classe base, `Second` é derivado de `First` e `Third` é derivado de `Second`. Todas as três têm finalizadores. Em `Main`, uma instância da classe mais derivada é criada. Quando o programa for executado, observe que os finalizadores das três classes são chamados automaticamente e em ordem, do mais derivado para o menos derivado.  
  
 [!code-cs[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_2.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IDisposable>   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Coleta de lixo](../../../standard/garbage-collection/index.md)

