---
title: Como tornar arquivos de modelo e mapeamento recursos inseridos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 98fb3ada369279a34ed08110644aabcbbe72a501
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a>Como tornar arquivos de modelo e mapeamento recursos inseridos
O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] permite que você implante o modelo e arquivos de mapeamento como recursos incorporados de um aplicativo. O assembly com o modelo inserido e os arquivos de mapeamento devem ser carregados no mesmo domínio de aplicativo que a conexão de entidade. Para obter mais informações, consulte [cadeias de caracteres de Conexão](../../../../../docs/framework/data/adonet/ef/connection-strings.md). Por padrão, o [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] ferramentas incorporem o modelo e os arquivos de mapeamento. Quando você definir manualmente o modelo e os arquivos de mapeamento, use este procedimento para garantir que os arquivos são implantados como recursos incorporados junto com um [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplicativo.  
  
> [!NOTE]
>  Para manter os recursos inseridos, você deverá repetir este procedimento sempre que os arquivos de modelo e mapeamento forem modificados.  
  
### <a name="to-embed-model-and-mapping-files"></a>Para inserir os arquivos de modelo e mapeamento  
  
1.  Em **Solution Explorer**, selecione o arquivo (. CSDL) conceitual.  
  
2.  No **propriedades** painel, defina **ação de compilação** para **recurso inserido**.  
  
3.  Repita as etapas 1 e 2 para o arquivo de armazenamento (.ssdl) e o arquivo de mapeamento (.msl).  
  
4.  Em **Solution Explorer**, duas vezes no arquivo App. config e, em seguida, modificar o `Metadata` parâmetro no `connectionString` atributo baseado em um dos seguintes formatos:  
  
    -   `Metadata=` `res://<assemblyFullName>/<resourceName>;`  
  
    -   `Metadata=` `res://*/<resourceName>;`  
  
    -   `Metadata=res://*;`  
  
     Para obter mais informações, consulte [cadeias de caracteres de Conexão](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  
  
## <a name="example"></a>Exemplo  
 A seguinte cadeia de conexão faz referência modelo inserido e arquivos de mapeamento para o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832). Esta cadeia de conexão é armazenada no arquivo App.config do projeto.  
  
  
  
## <a name="see-also"></a>Consulte também  
 [Modelando e mapeando](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [Como: definir a cadeia de caracteres de Conexão](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)  
 [Como: criar uma cadeia de caracteres de Conexão EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
 [ADO.NET Entity Data Model Tools](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527) (Ferramentas de modelo de dados de entidade do ADO.NET)
