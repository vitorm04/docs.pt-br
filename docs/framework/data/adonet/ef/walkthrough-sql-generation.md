---
title: 'Passo a passo: Geração SQL'
ms.date: 03/30/2017
ms.assetid: 16c38aaa-9927-4f3c-ab0f-81636cce57a3
ms.openlocfilehash: ab08b404dc60483a39e5c6ae56d82b63932c3f3e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766316"
---
# <a name="walkthrough-sql-generation"></a>Passo a passo: Geração SQL
Este tópico ilustra como geração SQL ocorre no [provedor exemplo](http://go.microsoft.com/fwlink/?LinkId=180616). A seguinte consulta SQL Entity usa o modelo que está incluído com o provedor exemplo:  
  
```  
SELECT  j1.ProductId, j1.ProductName, j1.CategoryName, j2.ShipCountry, j2.ProductId  
FROM (  SELECT P.ProductName, P.ProductId, P.Category.CategoryName  
        FROM NorthwindEntities.Products AS P) as j1  
INNER JOIN (SELECT OD.ProductId, OD.Order.ShipCountry as ShipCountry  
            FROM NorthwindEntities.OrderDetails AS OD) as j2  
            ON j1.ProductId == j2.ProductId   
```  
  
 A consulta gerencia a seguir árvore de comando de saída que é passado para o provedor:  
  
```  
DbQueryCommandTree  
|_Parameters  
|_Query : Collection{Record['C1'=Edm.Int32, 'ProductID'=Edm.Int32, 'ProductName'=Edm.String, 'CategoryName'=Edm.String, 'ShipCountry'=Edm.String, 'ProductID1'=Edm.Int32]}  
  |_Project  
    |_Input : 'Join4'  
    | |_InnerJoin  
    |   |_Left : 'Join1'  
    |   | |_LeftOuterJoin  
    |   |   |_Left : 'Extent1'  
    |   |   | |_Scan : dbo.Products  
    |   |   |_Right : 'Extent2'  
    |   |   | |_Scan : dbo.Categories  
    |   |   |_JoinCondition  
    |   |     |_  
    |   |       |_Var(Extent1).CategoryID  
    |   |       |_=  
    |   |       |_Var(Extent2).CategoryID  
    |   |_Right : 'Join3'  
    |   | |_LeftOuterJoin  
    |   |   |_Left : 'Extent3'  
    |   |   | |_Scan : dbo.OrderDetails  
    |   |   |_Right : 'Join2'  
    |   |   | |_LeftOuterJoin  
    |   |   |   |_Left : 'Extent4'  
    |   |   |   | |_Scan : dbo.Orders  
    |   |   |   |_Right : 'Extent5'  
    |   |   |   | |_Scan : dbo.InternationalOrders  
    |   |   |   |_JoinCondition  
    |   |   |     |_  
    |   |   |       |_Var(Extent4).OrderID  
    |   |   |       |_=  
    |   |   |       |_Var(Extent5).OrderID  
    |   |   |_JoinCondition  
    |   |     |_  
    |   |       |_Var(Extent3).OrderID  
    |   |       |_=  
    |   |       |_Var(Join2).Extent4.OrderID  
    |   |_JoinCondition  
    |     |_  
    |       |_Var(Join1).Extent1.ProductID  
    |       |_=  
    |       |_Var(Join3).Extent3.ProductID  
    |_Projection  
      |_NewInstance : Record['C1'=Edm.Int32, 'ProductID'=Edm.Int32, 'ProductName'=Edm.String, 'CategoryName'=Edm.String, 'ShipCountry'=Edm.String, 'ProductID1'=Edm.Int32]  
        |_Column : 'C1'  
        | |_1  
        |_Column : 'ProductID'  
        | |_Var(Join4).Join1.Extent1.ProductID  
        |_Column : 'ProductName'  
        | |_Var(Join4).Join1.Extent1.ProductName  
        |_Column : 'CategoryName'  
        | |_Var(Join4).Join1.Extent2.CategoryName  
        |_Column : 'ShipCountry'  
        | |_Var(Join4).Join3.Join2.Extent4.ShipCountry  
        |_Column : 'ProductID1'  
          |_Var(Join4).Join3.Extent3.ProductID  
```  
  
 Este tópico descreve como converter esta árvore de comando de saída nas instruções SQL.  
  
```  
SELECT   
1 AS [C1],   
[Extent1].[ProductID] AS [ProductID],   
[Extent1].[ProductName] AS [ProductName],   
[Extent2].[CategoryName] AS [CategoryName],   
[Join3].[ShipCountry] AS [ShipCountry],   
[Join3].[ProductID] AS [ProductID1]  
FROM   [dbo].[Products] AS [Extent1]  
LEFT OUTER JOIN [dbo].[Categories] AS [Extent2] ON [Extent1].[CategoryID] = [Extent2].[CategoryID]  
INNER JOIN    
(SELECT [Extent3].[OrderID] AS [OrderID1], [Extent3].[ProductID] AS [ProductID], [Extent3].[UnitPrice] AS [UnitPrice], [Extent3].[Quantity] AS [Quantity], [Extent3].[Discount] AS [Discount], [Join2].[OrderID2], [Join2].[CustomerID], [Join2].[EmployeeID], [Join2].[OrderDate], [Join2].[RequiredDate], [Join2].[ShippedDate], [Join2].[Freight], [Join2].[ShipName], [Join2].[ShipAddress], [Join2].[ShipCity], [Join2].[ShipRegion], [Join2].[ShipPostalCode], [Join2].[ShipCountry], [Join2].[OrderID3], [Join2].[CustomsDescription], [Join2].[ExciseTax]  
FROM  [dbo].[OrderDetails] AS [Extent3]  
LEFT OUTER JOIN    
      (SELECT [Extent4].[OrderID] AS [OrderID2], [Extent4].[CustomerID] AS [CustomerID], [Extent4].[EmployeeID] AS [EmployeeID], [Extent4].[OrderDate] AS [OrderDate], [Extent4].[RequiredDate] AS [RequiredDate], [Extent4].[ShippedDate] AS [ShippedDate], [Extent4].[Freight] AS [Freight], [Extent4].[ShipName] AS [ShipName], [Extent4].[ShipAddress] AS [ShipAddress], [Extent4].[ShipCity] AS [ShipCity], [Extent4].[ShipRegion] AS [ShipRegion], [Extent4].[ShipPostalCode] AS [ShipPostalCode], [Extent4].[ShipCountry] AS [ShipCountry], [Extent5].[OrderID] AS [OrderID3], [Extent5].[CustomsDescription] AS [CustomsDescription], [Extent5].[ExciseTax] AS [ExciseTax]  
FROM  [dbo].[Orders] AS [Extent4]  
LEFT OUTER JOIN [dbo].[InternationalOrders] AS [Extent5] ON [Extent4].[OrderID] = [Extent5].[OrderID]   
      ) AS [Join2] ON [Extent3].[OrderID] = [Join2].[OrderID2]   
   ) AS [Join3] ON [Extent1].[ProductID] = [Join3].[ProductID]  
```  
  
## <a name="first-phase-of-sql-generation-visiting-the-expression-tree"></a>Primeiro estágio de geração SQL: Visitar a árvore de expressão  
 A figura a seguir ilustra o inicial vazio o estado do visitante.  Em todo este tópico, somente as propriedades relevantes da explicação passo a passo são mostradas.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")  
  
 Quando o nó de projeto é visitado, VisitInputExpression é chamado sobre sua entrada (Join4), que causa a visitar de Join4 pelo método VisitJoinExpression. Porque este é um nível superior, se associa os retornos de IsParentAJoin e falsos um novo SqlSelectStatement (SelectStatement0) é criado e empurrado na pilha da declaração SELECT. Além disso, um novo escopo (scope0) é inserido na tabela de símbolo. Antes que a primeira entrada (deixada) do join foi visitada, “true” é empurrado na pilha de IsParentAJoin. Right before Join1, que é a entrada esquerda de Join4, é visitado, o estado do visitante é conforme mostrado na figura a seguir.  
  
 ![Diagrama de](../../../../../docs/framework/data/adonet/ef/media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")  
  
 Quando o método de visita de associação é chamado sobre Join4, IsParentAJoin é true, então reutiliza a instrução select SelectStatement0 atuais. Um novo escopo é inserido (scope1). Antes de visitar seu filho esquerdo, Extent1, outro verdadeiro é empurrado na pilha de IsParentAJoin.  
  
 Quando Extent1 é visitado, porque IsParentAJoin retorna true, retorna um SqlBuilder que contém “dbo []. Classes []”. O controle retorna para o método que Join4 visita. Uma entrada é aparecida de IsParentAJoin, e ProcessJoinInputResult é chamado, que anexa o resultado de visitar Extent1 para a cláusula de SelectStatement0. Um novo do símbolo, symbol_Extent1, para o nome de associação “Extent1” de entrada é criado, adicionado ao FromExtents de SelectStatement0, e também como” e “symbol_Extent1 são acrescentados à cláusula. Uma nova entrada é adicionada a AllExtentNames para “Extent1” com o valor de 0. Uma nova entrada é adicionada ao escopo atual na tabela de símbolo para associar “Extent1” com o símbolo symbol_Extent1. Symbol_Extent1 também é adicionado ao AllJoinExtents de SqlSelectStatement.  
  
 Antes que a entrada direita de Join1 está visitada, “LEFT OUTER JOIN” é adicionado à cláusula de SelectStatement0. Porque a entrada direita é uma expressão de verificação, verdadeira é empurrado novamente para a pilha de IsParentAJoin. O estado antes de entrada visitar a direita conforme mostrado na figura a seguir.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")  
  
 A entrada direita é processada da mesma forma como entrada esquerda. O estado após visitado entrada direita é mostrado na figura a seguir.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")  
  
 “False” seguir é empurrado na pilha de IsParentAJoin e == o Var de Var de condição de adição (Extent1) .CategoryID (Extent2) .CategoryID é processado. O Var (Extenent1) é resolvido <para symbol_Extent1> após pesquisa na tabela de símbolo. Porque a instância é resolvida para um símbolo simple, como resultado do processamento Var(Extent1). CategoryID, um SqlBuilder com \<symbol1 >. " CategoryID"será retornado. O outro lado de comparação é processado mesma forma, e o resultado de visitar a condição de associação é acrescentado à cláusula de SelectStatement1 e o valor “false” é aparecido a pilha de IsParentAJoin.  
  
 Com isso, Join1 foi processado completamente, e um escopo é aparecido da tabela de símbolo.  
  
 O controle retorna a processar Join4, o pai de Join1. Porque o filho reutilizou a instrução select, as extensões Join1 são substituídas por um único join o símbolo <joinSymbol_Join1>. Uma nova entrada também é adicionada à tabela de símbolo para associar Join1 com <o joinSymbol_Join1>.  
  
 O nó a seguir seja processado é Join3, como filhos de Join4. Porque é um filho à direita, “false” é empurrado para a pilha de IsParentAJoin. O estado do visitante é ilustrado nesse momento na figura a seguir.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")  
  
 Para Join3, IsParentAJoin retorna false e precisa-o de iniciar um novo SqlSelectStatement (SelectStatement1) e de empurrá-lo na pilha. O processamento continua como fez com o anterior o anterior, se associa um novo escopo é empurrado na pilha e os filhos são processados. O filho esquerdo é uma extensão (Extent3) e o filho adequado é uma união (Join2) que também precisa iniciar um novo SqlSelectStatement: SelectStatement2. Os filhos em Join2 são extensões e também são agregados em SelectStatement2.  
  
 O estado do visitante right after Join2 está visitado, mas antes que o após processamento (ProcessJoinInputResult) é feito é mostrado na figura a seguir:  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")  
  
 Na figura anterior, SelectStatement2 é mostrado como flutuante livre porque foi aparecido fora da pilha, mas ainda não a postagem processada pelo pai. Precisa ser adicionado à parte do pai, mas não é uma instrução SQL concluída sem uma cláusula SELECT. Assim, neste ponto, as colunas padrão (todas as colunas geradas por suas entradas) são adicionados à lista select pelo método AddDefaultColumns. AddDefaultColumns itera através dos símbolos em FromExtents e cada símbolo adiciona todas as colunas trazidas no escopo. Para um símbolo simples, ele tem o tipo do símbolo para recuperar todas as suas propriedades sejam adicionadas. Também preenche o dicionário de AllColumnNames com os nomes de coluna. O SelectStatement2 concluído é acrescentado à cláusula de SelectStatement1.  
  
 Em seguida, um novo join o símbolo é criado para representar Join2, é marcado como aninhado join e adicionou ao AllJoinExtents de SelectStatement1 e adicionou à tabela de símbolo.  Agora a condição de Join3, Var de adição (Extent3) .OrderID = Var (Join2). Extent4.OrderID, precisa ser processado. O processamento do lado esquerdo é semelhante à condição de adição de Join1. No entanto, o processamento do lado direito e “Var (Join2). Extent4.OrderID” é diferente porque se junte a ajuste é necessário.  
  
 A figura a seguir mostra o estado do visitante mesmo antes de DbPropertyExpression “Var (Join2). Extent4.OrderID” é processado.  
  
 Considere como “Var (Join2). Extent4.OrderID” é visitado. Primeiro, a propriedade “Var de instância (Join2). Extent4” é visitado, que é um outro DbPropertyExpression e está visitando seu instância Var Join2 (“”). Na parte superior a maioria de escopo na tabela de símbolo, “Join2” resolve <a joinSymbol_join2>. No método de visita para o processamento “Var de DbPropertyExpression (Join2). ” Aviso Extent4 que um símbolo do join foi retornada a visitar a instância e para ajuste é necessário.  
  
 Desde que está aninhado joins, nós pesquisamos a propriedade “Extent4” no dicionário de NameToExtent de símbolo de adição, resolvê-lo a <symbol_Extent4> e retornar um novo SymbolPair(<joinSymbol_join2>, <symbol_Extent4>). Como um par de símbolo é retornado de processamento de instância de “Var (Join2). Extent4.OrderID”, a propriedade “OrderID” é resolvido de ColumnPart do controle do símbolo (<symbol_Extent4>), que tenha uma lista de colunas de extensão que representa. Assim, “Var (Join2). Extent4.OrderID” é resolvido { <joinSymbol_Join2>, “. ”, <symbol_OrderID>}.  
  
 A condição de adição de Join4 é processada da mesma forma. O controle retorna para o método de VisitInputExpression que processou a parte superior a maioria de projeto. Examinando o FromExtents de SelectStatement0 retornado, a entrada é identificada como uma união, e remove as extensões originais e substituir-las com uma nova extensão com apenas o símbolo do join. A tabela de símbolo é atualizada e também a parte da projeção de Projeto é processada em seguida. Resolver propriedades e ajuste das extensões do join são como descrito anteriormente.  
  
 ![Diagram](../../../../../docs/framework/data/adonet/ef/media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")  
  
 Finalmente, o seguinte SqlSelectStatement é gerado:  
  
```  
SELECT:   
  "1", " AS ", "[C1]",  
  <symbol_Extent1>, ".", "[ProductID]", " AS ", "[ProductID]",   
  <symbol_Extent1>, ".", "[ProductName]", " AS ", "[ProductName]",  
  <symbol_Extent2>, ".", "[CategoryName]", " AS ", "[CategoryName]",  
  <joinSymbol_Join3>, ".", <symbol_ShipCountry>, " AS ", "[ShipCountry]",   
  <joinSymbol_Join3>, ".", <symbol_ProductID>, " AS ", "[ProductID1]"  
FROM: "[dbo].[Products]", " AS ", <symbol_Extent1>,   
        "LEFT OUTER JOIN ""[dbo].[Categories]", " AS ", <symbol_Extent2>, " ON ", <symbol_Extent1>, ".", "[CategoryID]", " = ", <symbol_Extent2>, ".", "[CategoryID]",   
        "INNER JOIN ",   
        " (", SELECT:   
           <symbol_Extent3>, ".", "[OrderID]", " AS ", <symbol_OrderID>, ",   
              <symbol_Extent3>, ".", "[ProductID]", " AS ", <symbol_ProductID>, ...,  
         <joinSymbol_Join2>, ".", <symbol_OrderID_2>, ", ",   
           <joinSymbol_Join2>, ".", <symbol_CustomerID>, ....,    
        <joinSymbol_Join2>, ".", <symbol_OrderID_3>,   
<joinSymbol_Join2>, ".", <symbol_CustomsDescription>,   
<joinSymbol_Join2>, ".", <symbol_ExciseTax>  
FROM: "[dbo].[OrderDetails]", " AS ", <symbol_Extent3>,   
"LEFT OUTER JOIN ",   
" (", SELECT:   
<symbol_Extent4>, ".", "[OrderID]", " AS ", <symbol_OrderID_2>,   
<symbol_Extent4>, ".", "[CustomerID]", " AS ", <symbol_CustomerID>, ...  
<symbol_Extent5>, ".", "[OrderID]", " AS ", <symbol_OrderID_3>,  
<symbol_Extent5>, ".", "[CustomsDescription]", " AS ", <symbol_CustomsDescription>,  
<symbol_Extent5>, ".", "[ExciseTax]", " AS ", <symbol_ExciseTax>  
FROM: "[dbo].[Orders]", " AS ", <symbol_Extent4>,  
"LEFT OUTER JOIN ", , "[dbo].[InternationalOrders]", " AS ", <symbol_Extent5>,   
" ON ", <symbol_Extent4>, ".", "[OrderID]", " = ", , <symbol_Extent5>, ".", "[OrderID]"  
" )", " AS ", <joinSymbol_Join2>, " ON ", , , <symbol_Extent3>, ".", "[OrderID]", " = ", , <joinSymbol_Join2>, ".", <symbol_OrderID_2>  
" )", " AS ", <joinSymbol_Join3>, " ON ", , , <symbol_Extent1>, ".", "[ProductID]", " = ", , <joinSymbol_Join3>, ".", <symbol_ProductID>  
```  
  
### <a name="second-phase-of-sql-generation-generating-the-string-command"></a>Segundo fase de geração SQL: Gerando o comando de cadeia de caracteres  
 A segunda etapa gerencie nomes reais dos símbolos, e nós centramo-nos apenas sobre os símbolos que representam as colunas chamadas “OrderID”, porque nesse caso um conflito precisa ser resolvido. Esses são realçadas no SqlSelectStatement. Observe que os sufixos usados na figura são enfatizar somente essas instâncias são diferentes, não para representar os novos nomes, porque seus nomes finais (possivelmente formulário diferente os nomes originais) não foram atribuídos nesse estágio ainda.  
  
 O primeiro símbolo encontrado que precisa ser renomeado é <symbol_OrderID>. O novo nome é atribuído como “OrderID1”, 1 é marcado como o último usou o sufixo” para “OrderID e o símbolo é marcado como não precisando renomear. Em seguida, o primeiro uso <de symbol_OrderID_2> for encontrado. É renomeado para usar o sufixo disponível a OrderID2 (“”) e marcado como novamente não precisando renomear, de modo que as próximas vezes onde ela é usado não pegue renomeado. Isso é feito para <symbol_OrderID_3> muito.  
  
 No final da segunda etapa, a instrução SQL final é gerada.  
  
## <a name="see-also"></a>Consulte também  
 [Geração de SQL no provedor exemplo](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)
