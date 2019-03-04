---
title: Finalizadores – Guia de Programação em C#
ms.custom: seodec18
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 19c1f754aaef66197b033a68bc215255511cd618
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202880"
---
# <a name="finalizers-c-programming-guide"></a>Finalizadores (Guia de Programação em C#)
Os finalizadores (que também são chamados de **destruidores**) são usados para executar qualquer limpeza final necessária, quando uma instância da classe está sendo coletada pelo coletor de lixo.  
  
## <a name="remarks"></a>Comentários  
  
-   Os finalizadores não podem ser definidos em structs. Eles são usados somente com classes.  
  
-   Uma classe pode ter somente um finalizador.  
  
-   Os finalizadores não podem ser herdados ou sobrecarregados.  
  
-   Os finalizadores não podem ser chamados. Eles são invocados automaticamente.  
  
-   Um finalizador não usa modificadores ou não tem parâmetros.  
  
 Por exemplo, o seguinte é uma declaração de um finalizador para a classe `Car`.
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

Um finalizador também pode ser implementado como uma definição do corpo da expressão, como mostra o exemplo a seguir.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
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
  
 O programador não tem controle sobre quando o finalizador é chamado porque isso é determinado pelo coletor de lixo. O coletor de lixo procura objetos que não estão mais sendo usados pelo aplicativo. Se considerar um objeto qualificado para finalização, ele chamará o finalizador (se houver) e recuperará a memória usada para armazenar o objeto. 
 
 Em aplicativos .NET Framework (mas não em aplicativos .NET Core), os finalizadores também são chamados quando o programa é encerrado. 
  
 É possível forçar a coleta de lixo chamando <xref:System.GC.Collect%2A>, mas na maioria das vezes, isso deve ser evitado porque pode criar problemas de desempenho.  
  
## <a name="using-finalizers-to-release-resources"></a>Usar finalizadores para liberar recursos  
 Em geral, o C# não demanda tanto gerenciamento de memória quanto é necessário quando você desenvolve usando uma linguagem que não tem como destino um tempo de execução com coleta de lixo. Isso ocorre porque o coletor de lixo do .NET Framework gerencia implicitamente a alocação e a liberação de memória para seus objetos. No entanto, quando seu aplicativo encapsula recursos não gerenciados, como janelas, arquivos e conexões de rede, você deve usar finalizadores para liberar esses recursos. Quando o objeto está qualificado para finalização, o coletor de lixo executa o método `Finalize` do objeto.  
  
## <a name="explicit-release-of-resources"></a>Liberação explícita de recursos  
 Se seu aplicativo estiver usando um recurso externo caro, também será recomendável fornecer uma maneira de liberar explicitamente o recurso antes que o coletor de lixo libere o objeto. Você faz isso implementando um método `Dispose` da interface <xref:System.IDisposable> que executa a limpeza necessária para o objeto. Isso pode melhorar consideravelmente o desempenho do aplicativo. Mesmo com esse controle explícito sobre os recursos, o finalizador se tornará uma proteção usada para limpar os recursos se a chamada para o método `Dispose` falhar.  
  
 Para obter mais detalhes sobre limpeza de recursos, consulte os seguintes tópicos:  
  
-   [Limpando recursos não gerenciados](../../../standard/garbage-collection/unmanaged.md)  
  
-   [Implementando um método dispose](../../../standard/garbage-collection/implementing-dispose.md)  
  
-   [Instrução using](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria três classes que compõem uma cadeia de herança. A classe `First` é a classe base, `Second` é derivado de `First` e `Third` é derivado de `Second`. Todas as três têm finalizadores. Em `Main`, uma instância da classe mais derivada é criada. Quando o programa for executado, observe que os finalizadores das três classes são chamados automaticamente e em ordem, do mais derivado para o menos derivado.  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a>Especificação da linguagem C#  

Para obter mais informações, confira a seção [Destruidores](~/_csharplang/spec/classes.md#destructors) na [Especificação da linguagem C#](../../language-reference/language-specification/index.md).
  
## <a name="see-also"></a>Consulte também

- <xref:System.IDisposable>
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Coleta de lixo](../../../standard/garbage-collection/index.md)
