---
title: Considerações de implantação (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 3a847a22-4eb8-4565-b18b-453bbca070db
ms.openlocfilehash: b240b7da1d05e1bf02e31acc3c99b16a908a6add
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689871"
---
# <a name="deployment-considerations-entity-framework"></a>Considerações de implantação (Entity Framework)
Este tópico fornece informações sobre como implantar aplicativos que usam o ADO.NET Entity Framework para acesso a dados. Para obter mais informações sobre o Entity Framework, consulte [Introdução ao](../../../../../docs/framework/data/adonet/ef/getting-started.md).  
  
 Entity Framework fornece um conjunto de ferramentas que se integram com e facilitam ficar no Visual Studio. Para obter mais informações, consulte [ferramentas de modelo de dados de entidade ADO.NET](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527). Este tópico não descreve como usar tecnologias específicas para implantar um aplicativo baseado no objeto.  
  
 Visual Studio fornece recursos para distribuir e implantar aplicativos, como a implantação de ClickOnce. Para obter mais informações, consulte [Implantando aplicativos e componentes](/visualstudio/deployment/deploying-applications-services-and-components) na documentação do Visual Studio.  
  
 As seguintes condições se aplicam quando você implantar um aplicativo que usa Entity Framework:  
  
-   Entity Framework é um componente.NET Framework que começa com o .NET Framework 3.5 Service Pack 1 (SP1). Você deve garantir que o .NET Framework 3.5 SP1 ou posterior são instalados quando implantar uma entidade framework com o aplicativo.  
  
-   Quando um modelo conceitual é gerado pelo assistente de Modelo de Dados de Entidade, uma cadeia de conexão é criada no arquivo de configuração do aplicativo. O modelo e arquivos de mapeamento podem ser inseridos como recursos de aplicativo ou pode ser copiado para o diretório de saída. Por padrão, são implantados como recursos inseridos do aplicativo. Use a propriedade de `Metadata Artifact Processing` do arquivo de designer de entidade para selecionar uma dessas opções. Para obter mais informações, confira [Como: Copie o modelo e arquivos de mapeamento para o diretório de saída](https://msdn.microsoft.com/library/e2c9820f-1705-457e-9fdb-8b289f3179b4).  
  
-   Certifique-se de que o modelo e informações de mapeamento (expressa na linguagem de definição de esquema conceitual (CSDL), na linguagem de definição de esquema de armazenamento (SSDL), e na linguagem de especificação (MSL) de mapeamento) são implantados juntamente com o aplicativo e no local especificado pela cadeia de conexão. Para saber mais, confira [Cadeias de conexão](../../../../../docs/framework/data/adonet/ef/connection-strings.md).  
  
-   Quando você insere o modelo e informações de mapeamento como recursos de aplicativo, você deve recompilar e reimplantar o aplicativo cada vez que o modelo conceitual é atualizado.  
  
-   Porque Entity Framework é um componente.NET Framework, pode ser redistribuído com o seu aplicativo como permitido pelo contrato de licença do .NET Framework.  
  
## <a name="see-also"></a>Consulte também
- [Entity Framework do ADO.NET](../../../../../docs/framework/data/adonet/ef/index.md)
- [Considerações de desenvolvimento e implantação](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)
