---
title: 'Como: definir a cadeia de conexão'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: a78158c7553c0b479b935e3b94931313df912c2f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854650"
---
# <a name="how-to-define-the-connection-string"></a>Como: definir a cadeia de conexão

Este tópico mostra como definir a cadeia de conexão que é usada ao se conectar a um modelo conceitual. Este tópico se baseia no modelo conceitual de [vendas AdventureWorks](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) . O modelo de vendas AdventureWorks é usado em todos os tópicos relacionados à tarefa na documentação do Entity Framework. Este tópico pressupõe que você já tenha configurado o Entity Framework e definido o modelo de vendas AdventureWorks. Para obter mais informações, confira [Como: Defina manualmente o modelo e os arquivos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))de mapeamento. Os procedimentos neste tópico também estão incluídos em [como: Configurar manualmente um projeto](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))de Entity Framework.

> [!NOTE]
> Se você usar o assistente de Modelo de Dados de Entidade em um projeto do Visual Studio, ele gerará automaticamente um arquivo. edmx e configurará o projeto para usar o Entity Framework. Para obter mais informações, confira [Como: Usar o assistente de Modelo de Dados de Entidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))

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

## <a name="see-also"></a>Consulte também

- [Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100)) (Início rápido)
- [Como: Criar um novo arquivo. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))
- [ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) (Ferramentas de modelo de dados de entidade do ADO.NET)
