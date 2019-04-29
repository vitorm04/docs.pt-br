---
title: 'Como: definir a cadeia de conexão'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 7fb722acbb13b3502d004978581701cc70118ff8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606095"
---
# <a name="how-to-define-the-connection-string"></a>Como: definir a cadeia de conexão

Este tópico mostra como definir a cadeia de conexão que é usada ao se conectar a um modelo conceitual. Este tópico se baseia a [vendas do AdventureWorks](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) modelo conceitual. O Modelo de Vendas do AdventureWorks é usado em todos os tópicos relacionados a tarefas na documentação do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Este tópico pressupõe que você já tenha configurado o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] e definidos pelo modelo de vendas AdventureWorks. Para obter mais informações, confira [Como: Definir o modelo e arquivos de mapeamento manualmente](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)). Os procedimentos neste tópico também estão incluídos no [como: Configurar manualmente um projeto do Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).

> [!NOTE]
> Se você usar o [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] assistente em um projeto do Visual Studio, ele gera um arquivo. edmx e configura automaticamente o projeto para usar o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Para obter mais informações, confira [Como: Use o Assistente de modelo de dados de entidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))

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

Se seu projeto não tiver um arquivo de configuração de aplicativo, você pode adicionar um selecionando **Adicionar Novo Item** da **Project** menu, selecionando o **geral** categoria, selecionando **arquivo de configuração de aplicativo**e, em seguida, clicando em **Add**.

## <a name="see-also"></a>Consulte também

- [Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100)) (Início rápido)
- [Como: Crie um novo arquivo. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) (Ferramentas de modelo de dados de entidade do ADO.NET)
