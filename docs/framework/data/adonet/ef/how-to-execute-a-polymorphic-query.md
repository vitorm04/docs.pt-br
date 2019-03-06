---
title: 'Como: Executar uma consulta Polimorfo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: 08ae5722267ef781ed6bee59c7895269f63a75e5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355527"
---
# <a name="how-to-execute-a-polymorphic-query"></a>Como: Executar uma consulta Polimorfo

Este tópico mostra como executar um polimórfico [!INCLUDE[esql](../../../../../includes/esql-md.md)] consultar usando o [OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operador.

### <a name="to-run-the-code-in-this-example"></a>Para executar o código nesse exemplo

1. Adicione a [modelo de escola](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) ao seu projeto e configurar seu projeto para usar o Entity Framework. Para obter mais informações, confira [Como: Use o Assistente de modelo de dados de entidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).

2. Na página de código do seu aplicativo, adicione as seguintes instruções `using` (`Imports` no Visual Basic):

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. Modificar o modelo conceitual para ter uma herança de tabela por hierarquia, seguindo as etapas em [passo a passo: Mapeamento de herança - tabela por hierarquia](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).

## <a name="example"></a>Exemplo

O seguinte exemplo usa um operador de OFTYPE para obter e exibir uma coleção somente de `OnsiteCourses` de uma coleção de `Courses`.

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a>Consulte também

- [Provedor EntityClient para Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
- [Entity SQL Language](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) (Linguagem SQL de entidade)
