---
title: 'Como: definir a cadeia de conexão'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 9b029644e0d4e4c7467fbe1e1144579e6edb3478
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536204"
---
# <a name="how-to-define-the-connection-string"></a>Como: definir a cadeia de conexão

Este tópico mostra como definir a cadeia de conexão que é usada ao se conectar a um modelo conceitual. Este tópico se baseia no modelo conceitual de [vendas AdventureWorks](/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) . O modelo de vendas AdventureWorks é usado em todos os tópicos relacionados à tarefa na documentação do Entity Framework. Este tópico pressupõe que você já tenha configurado o Entity Framework e definido o modelo de vendas AdventureWorks. Para obter mais informações, consulte [como definir manualmente o modelo e os arquivos de mapeamento](/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)). Os procedimentos neste tópico também estão incluídos em [como configurar manualmente um projeto de Entity Framework](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).

> [!NOTE]
> Se você usar o assistente de Modelo de Dados de Entidade em um projeto do Visual Studio, ele gerará automaticamente um arquivo. edmx e configurará o projeto para usar o Entity Framework. Para obter mais informações, consulte [como: usar o assistente de modelo de dados de entidade](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).

## <a name="to-define-the-entity-framework-connection-string"></a>Para definir a cadeia de conexão do Entity Framework

- Abra o arquivo de configuração do aplicativo de projeto (app.config) e adicione a seguinte cadeia de conexão:

```xml
<connectionStrings>
    <add name="AdventureWorksEntities"
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

Se o seu projeto não tiver um arquivo de configuração de aplicativo, você poderá adicionar um, selecionando **Adicionar novo item** no menu **projeto** , selecionando a categoria **geral** , selecionando **arquivo de configuração de aplicativo**e clicando em **Adicionar**.

## <a name="see-also"></a>Confira também

- [Início rápido](/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [Como: criar um novo arquivo. edmx](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) (Ferramentas de modelo de dados de entidade do ADO.NET)
