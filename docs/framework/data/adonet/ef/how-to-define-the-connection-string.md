---
title: Como definir a cadeia de conexão
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: e5b675a50f883825cce97275048447b79b64cc97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150565"
---
# <a name="how-to-define-the-connection-string"></a>Como definir a cadeia de conexão

Este tópico mostra como definir a cadeia de conexão que é usada ao se conectar a um modelo conceitual. Este tópico é baseado no modelo conceitual [AdventureWorks Sales.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) O Modelo de Vendas AdventureWorks é usado em todos os tópicos relacionados à tarefa na documentação Entity Framework. Este tópico pressupõe que você já configurou o Framework entity e definiu o Modelo de Vendas AdventureWorks. Para obter mais informações, [consulte Como definir manualmente os arquivos de modelo e mapeamento](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)). Os procedimentos neste tópico também estão incluídos em [Como: Configurar manualmente um Projeto Estrutura de Entidades](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).

> [!NOTE]
> Se você usar o Assistente de Modelo de Dados de Entidade em um projeto do Visual Studio, ele gerará automaticamente um arquivo .edmx e configurará o projeto para usar o Framework entity. Para obter mais informações, consulte [Como: Usar o Assistente do Modelo de Dados da Entidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).

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

Se o seu projeto não tiver um arquivo de configuração de aplicativo, você pode adicionar um selecionando **Adicionar novo item** no menu **Projeto,** selecionando a categoria **Geral,** selecionando **Arquivo de configuração de aplicativo**e, em seguida, clicando em **Adicionar**.

## <a name="see-also"></a>Confira também

- [Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))
- [Como: Criar um novo arquivo .edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) (Ferramentas de modelo de dados de entidade do ADO.NET)
