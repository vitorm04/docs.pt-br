---
title: "Trabalhando com a linguagem de definição de dados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8b363105f0dd6978d4e59678fb7cd1b3f1d721df
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="working-with-data-definition-language"></a>Trabalhando com a linguagem de definição de dados
Começando com o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] versão 4, o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] oferece suporte a linguagem de definição de dados (DDL). Isso permite que você crie ou exclua uma instância do banco de dados com base na cadeia de conexão e nos metadados do modelo de armazenamento (SSDL).  
  
 Os métodos a seguir no <xref:System.Data.Objects.ObjectContext> usam a cadeia de conexão e o conteúdo SSDL para criar ou excluir o banco de dados, verificar se o banco de dados existe e exibir o script DDL gerado:  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
>  A execução de comandos DDL pressupõe permissões suficientes.  
  
 Os métodos listados anteriormente delegam a maioria do trabalho para o provedor de dados ADO.NET subjacente. É responsabilidade do provedor garantir que a convenção de nomenclatura usada para gerar objetos de banco de dados seja consistente com as convenções usadas nas consultas e atualizações.  
  
 O exemplo a seguir mostra como gerar o banco de dados com base no modelo existente. Ele também adiciona um novo objeto de entidade ao contexto de objeto e os salva no banco de dados.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-define-a-database-based-on-the-existing-model"></a>Para definir um banco de dados com base no modelo existente  
  
1.  Crie um aplicativo de console.  
  
2.  Adicione um modelo existente ao seu aplicativo.  
  
    1.  Adicionar um modelo vazio chamado `SchoolModel`. Para criar um modelo vazio, consulte o [como: criar um novo arquivo de EDMX](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2) tópico.  
  
     O arquivo SchoolModel.edmx é adicionado ao projeto.  
  
    1.  Copiar o conceitual, armazenamento e mapeamento de conteúdo para o modelo de escola do [modelo School](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac) tópico.  
  
    2.  Abra o arquivo SchoolModel.edmx e cole o conteúdo nas marcas `edmx:Runtime`.  
  
3.  Adicione o seguinte código à função principal. O código inicializa a cadeia de conexão ao servidor de banco de dados, exibe o script DDL, cria o banco de dados, adiciona uma nova entidade ao contexto e salva as alterações no banco de dados.  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
