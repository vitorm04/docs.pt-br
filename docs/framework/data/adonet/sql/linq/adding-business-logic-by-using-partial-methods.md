---
title: Adicionando a lógica comercial usando métodos parciais
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 8ea345f01c68f8c962069a3e9fdca7feff84c5c0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="adding-business-logic-by-using-partial-methods"></a>Adicionando a lógica comercial usando métodos parciais
Você pode personalizar o Visual Basic e c# gerado código no seu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projetos usando *métodos parciais*. O código que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] gerencia define assinaturas como uma parte de um método parcial. Se você deseja implementar o método, você pode adicionar seu próprio método parcial. Se você não adiciona sua própria implementação, o compilador descarta a assinatura parcial de métodos e chama os métodos padrão em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
>  Se você estiver usando o Visual Studio, você pode usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para adicionar outras personalizações e validação a classes de entidade.  
  
 Por exemplo, o mapeamento padrão para a classe de `Customer` na base de dados de exemplo Northwind inclui o seguinte método parcial:  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 Você pode implementar seu próprio método adicionando o código como o seguinte a sua própria classe parcial de `Customer` :  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 Essa abordagem é usada normalmente em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para substituir os métodos padrão para `Insert`, `Update`, `Delete`e para validar propriedades durante eventos de ciclo de vida do objeto.  
  
 Para obter mais informações, consulte [métodos parciais](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) ou [partial (método) (referência de c#)](~/docs/csharp/language-reference/keywords/partial-method.md) (c#).  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir mostra como `ExampleClass` primeiro pode ser definido por uma ferramenta de geração como SQLMetal e em seguida, como você pode implementar apenas um dos dois métodos.  
  
### <a name="code"></a>Código  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir usa a relação entre `Shipper` e entidades de `Order` . Observe entre os métodos métodos parciais, `InsertShipper` e `DeleteShipper`. Esses métodos substituem os métodos parciais padrão fornecidos pelo [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapeamento.  
  
### <a name="code"></a>Código  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Realizando e enviando alterações de dados](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [Personalizando as operações de inserção, atualização e exclusão](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
