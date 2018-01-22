---
title: "Considerações de implantação (Entity Framework)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a847a22-4eb8-4565-b18b-453bbca070db
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d38f90822746c08d576879ab35fa0984e439640b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="deployment-considerations-entity-framework"></a>Considerações de implantação (Entity Framework)
Este tópico fornece informações sobre como implantar aplicativos que usam o ADO.NET Entity Framework para acesso a dados. Para obter mais informações sobre o Entity Framework, consulte [Introdução](../../../../../docs/framework/data/adonet/ef/getting-started.md).  
  
 Entity Framework fornece um conjunto de ferramentas que se integram com e facilitam ficar no Visual Studio. Para obter mais informações, consulte [ferramentas de modelo de dados de entidade ADO.NET](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527). Este tópico não descreve como usar tecnologias específicas para implantar um aplicativo baseado no objeto.  
  
 Visual Studio fornece recursos para distribuir e implantar aplicativos, como a implantação de ClickOnce. Para obter mais informações, consulte [implantação de aplicativos e componentes](/visualstudio/deployment/deploying-applications-services-and-components) na documentação do Visual Studio.  
  
 As seguintes condições se aplicam quando você implantar um aplicativo que usa Entity Framework:  
  
-   Entity Framework é um componente.NET Framework que começa com o .NET Framework 3.5 Service Pack 1 (SP1). Você deve garantir que o .NET Framework 3.5 SP1 ou posterior são instalados quando implantar uma entidade framework com o aplicativo.  
  
-   Quando um modelo conceitual é gerado pelo assistente de Modelo de Dados de Entidade, uma cadeia de conexão é criada no arquivo de configuração do aplicativo. O modelo e arquivos de mapeamento podem ser inseridos como recursos de aplicativo ou pode ser copiado para o diretório de saída. Por padrão, são implantados como recursos inseridos do aplicativo. Use a propriedade de `Metadata Artifact Processing` do arquivo de designer de entidade para selecionar uma dessas opções. Para obter mais informações, consulte [como: copiar arquivos de modelo e mapeamento para o diretório de saída](http://msdn.microsoft.com/library/e2c9820f-1705-457e-9fdb-8b289f3179b4).  
  
-   Certifique-se de que o modelo e informações de mapeamento (expressa na linguagem de definição de esquema conceitual (CSDL), na linguagem de definição de esquema de armazenamento (SSDL), e na linguagem de especificação (MSL) de mapeamento) são implantados juntamente com o aplicativo e no local especificado pela cadeia de conexão. Para saber mais, confira [Cadeias de conexão](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  
  
-   Quando você insere o modelo e informações de mapeamento como recursos de aplicativo, você deve recompilar e reimplantar o aplicativo cada vez que o modelo conceitual é atualizado.  
  
-   Porque Entity Framework é um componente.NET Framework, pode ser redistribuído com o seu aplicativo como permitido pelo contrato de licença do .NET Framework.  
  
## <a name="see-also"></a>Consulte também  
 [Entity Framework do ADO.NET](../../../../../docs/framework/data/adonet/ef/index.md)  
 [Considerações de desenvolvimento e implantação](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)
