---
title: "Destruidores (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "~ [C#], em destruidores"
  - "Linguagem C#, destruidores"
  - "destruidores [C#]"
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Destruidores (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Destruidores são usadas para instâncias de classes de destruct.  
  
## Comentários  
  
-   Destruidores não podem ser definidas em estruturas.  Eles são usados somente com classes.  
  
-   Uma classe só pode ter um destruidor.  
  
-   Destruidores não podem ser herdadas ou sobrecarregados.  
  
-   Destruidores não podem ser chamados.  Eles são invocados automaticamente.  
  
-   Um destruidor não leva modificadores nem tem parâmetros.  
  
 Por exemplo, a seguir está uma declaração de um destruidor da classe `Car`:  
  
 [!code-cs[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_1.cs)]  
  
 O destruidor implicitamente chama <xref:System.Object.Finalize%2A> na classe base do objeto.  Portanto, o código anterior do destruidor implicitamente é convertido para o código a seguir:  
  
```  
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
  
 Isso significa que o `Finalize` método é chamado recursivamente para todas as instâncias da cadeia de herança, da maioria derivada para derivado de menos.  
  
> [!NOTE]
>  Destruidores vazios não devem ser usados.  Quando uma classe contém um destruidor, uma entrada é criada na `Finalize` fila.  Quando o destruidor é chamado, o coletor de lixo é chamado para processar a fila.  Se o destruidor estiver vazio, isso apenas causa uma perda desnecessária de desempenho.  
  
 O programador não tem controle sobre quando o destruidor é chamado porque isso é determinado pelo coletor de lixo.  O coletor de lixo procura objetos que não estão sendo usados pelo aplicativo.  Se um objeto considera elegível para destruição, ele chama o destruidor \(se houver\) e recupera a memória usada para armazenar o objeto.  Destruidores também são chamados quando o programa é encerrado.  
  
 É possível forçar a coleta de lixo chamando <xref:System.GC.Collect%2A>, mas na maioria das vezes, isso deve ser evitado porque pode criar problemas de desempenho.  
  
## Usar destruidores para recursos de lançamento  
 Em geral, o C\# não requer tanto gerenciamento de memória como é necessário quando você desenvolve com uma linguagem que não tem um tempo de execução com coleta de lixo.  Isso ocorre porque o.NET Framework coletor de lixo implicitamente gerencia a alocação e liberação de memória para os objetos.  No entanto, quando seu aplicativo encapsula recursos não gerenciados, como o windows, arquivos e conexões de rede, você deve usar destruidores para liberar esses recursos.  Quando o objeto é qualificado para destruição, o coletor de lixo executa o `Finalize` método do objeto.  
  
## Versão explícita de recursos  
 Se seu aplicativo estiver usando um recurso externo caro, também é recomendável que você fornecer uma maneira para liberar explicitamente o recurso antes que o coletor de lixo libera o objeto.  Faz isso implementando uma `Dispose` método a partir do <xref:System.IDisposable> interface que executa a limpeza necessária para o objeto.  Isso pode aumentar consideravelmente o desempenho do aplicativo.  Mesmo com esse controle explícito sobre recursos, o destruidor se torna uma salvaguarda para limpar recursos, se a chamada para o `Dispose` falha no método.  
  
 Para obter mais detalhes sobre a limpeza de recursos, consulte os tópicos a seguir:  
  
-   [Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md)  
  
-   [Implementing a Dispose Method](../Topic/Implementing%20a%20Dispose%20Method.md)  
  
-   [Instrução using](../../../visual-basic/language-reference/statements/using-statement.md)  
  
## Exemplo  
 O exemplo a seguir cria três classes que compõem uma cadeia de herança.  A classe `First` é a classe base, `Second` é derivada de `First`, e `Third` é derivada de `Second`.  Todas três tem destruidores.  Na `Main()`, uma instância da classe derivada para a maioria é criada.  Quando o programa é executado, observe que os destruidores para as três classes são chamados automaticamente e em ordem, da maioria derivada para derivado de menos.  
  
 [!code-cs[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_2.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 <xref:System.IDisposable>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Garbage Collection](../Topic/Garbage%20Collection.md)