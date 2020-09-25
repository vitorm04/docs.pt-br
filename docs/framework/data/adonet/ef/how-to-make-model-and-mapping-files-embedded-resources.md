---
title: 'Como: tornar arquivos de modelo e mapeamento recursos inseridos'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 8496dcad5422d1a45af52e58325efd360768da34
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198282"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a>Como: tornar arquivos de modelo e mapeamento recursos inseridos

O Entity Framework permite que você implante arquivos de modelo e de mapeamento como recursos incorporados de um aplicativo. O assembly com o modelo inserido e os arquivos de mapeamento devem ser carregados no mesmo domínio de aplicativo que a conexão de entidade. Para saber mais, confira [Cadeias de conexão](connection-strings.md). Por padrão, as ferramentas de Modelo de Dados de Entidade inserem o modelo e os arquivos de mapeamento. Ao definir manualmente o modelo e os arquivos de mapeamento, use este procedimento para garantir que os arquivos sejam implantados como recursos incorporados junto com um aplicativo Entity Framework.  
  
> [!NOTE]
> Para manter os recursos inseridos, você deverá repetir este procedimento sempre que os arquivos de modelo e mapeamento forem modificados.  
  
### <a name="to-embed-model-and-mapping-files"></a>Para inserir os arquivos de modelo e mapeamento  
  
1. Em **Gerenciador de soluções**, selecione o arquivo conceitual (. CSDL).  
  
2. No painel **Propriedades** , defina **ação de compilação** como **recurso incorporado**.  
  
3. Repita as etapas 1 e 2 para o arquivo de armazenamento (.ssdl) e o arquivo de mapeamento (.msl).  
  
4. Em **Gerenciador de soluções**, clique duas vezes no arquivo App.config e modifique o `Metadata` parâmetro no `connectionString` atributo com base em um dos seguintes formatos:  
  
    - `Metadata=` `res://<assemblyFullName>/<resourceName>;`  
  
    - `Metadata=` `res://*/<resourceName>;`  
  
    - `Metadata=res://*;`  
  
     Para saber mais, confira [Cadeias de conexão](connection-strings.md).  
  
## <a name="example"></a>Exemplo  

 A cadeia de conexão a seguir faz referência a arquivos de mapeamento e modelo inseridos para o [modelo de vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Esta cadeia de conexão é armazenada no arquivo App.config do projeto.  

## <a name="see-also"></a>Veja também

- [Modelando e mapeando](modeling-and-mapping.md)
- [Como: definir a cadeia de conexão](how-to-define-the-connection-string.md)
- [Como: criar uma cadeia de conexão EntityConnection](how-to-build-an-entityconnection-connection-string.md)
- [Ferramentas de Modelo de Dados de Entidade de ADO.NET](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
