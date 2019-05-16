---
title: 'Como: Gerar manualmente as Classes de serviço de dados do cliente (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: fdca85360e34d6854604103c9d0ac22c5b829cf5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634017"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a>Como: Gerar manualmente as Classes de serviço de dados do cliente (WCF Data Services)
WCF Data Services se integra com o Visual Studio para que você possa gerar classes de serviço de dados do cliente automaticamente quando você usa o **adicionar referência de serviço** caixa de diálogo para adicionar uma referência a um serviço de dados em um projeto do Visual Studio. Para obter mais informações, confira [Como: Adicionar uma referência de serviço de dados](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md). Você pode gerar também manualmente as mesmas classes de serviço de dados do cliente usando a ferramenta de geração de código, `DataSvcUtil.exe`. Essa ferramenta, que está incluída com o WCF Data Services, gera classes do .NET Framework da definição de serviço de dados. Ele também pode ser usado para gerar classes de serviço de dados do arquivo de modelo conceitual (. CSDL) e do arquivo. edmx que representa um modelo do Entity Framework em um projeto do Visual Studio.

 O exemplo neste tópico cria classes de serviço de dados do cliente com base no serviço de dados de exemplo Northwind. Esse serviço é criado quando você concluir o [início rápido do WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Alguns exemplos neste tópico requerem o arquivo de modelo conceitual para o modelo do Northwind. Para obter mais informações, confira [Como: Use EdmGen.exe para gerar o modelo e arquivos de mapeamento](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md). Alguns exemplos neste tópico exigem o arquivo. edmx para o modelo do Northwind. Para obter mais informações, consulte [visão geral do arquivo. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).

### <a name="to-generate-c-classes-that-support-data-binding"></a>Para gerar classes c# que dão suporte à vinculação de dados

- No prompt de comando, execute o seguinte comando sem quebras de linha:

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  Você deve substituir o valor fornecido para o `/uri:` parâmetro com o URI de sua instância do serviço de dados de exemplo Northwind.

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a>Para gerar classes de Visual Basic que suportam associação de dados

- No prompt de comando, execute o seguinte comando sem quebras de linha:

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  Você deve substituir o valor fornecido para o `/uri:` parâmetro com o URI de sua instância do serviço de dados de exemplo Northwind.

### <a name="to-generate-c-classes-based-on-the-service-uri"></a>Para gerar classes c# com base no URI de serviço

- No prompt de comando, execute o seguinte comando sem quebras de linha:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  Você deve substituir o valor fornecido para o `/uri:` parâmetro com o URI de sua instância do serviço de dados de exemplo Northwind.

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a>Para gerar classes do Visual Basic com base no URI de serviço

- No prompt de comando, execute o seguinte comando sem quebras de linha:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  Você deve substituir o valor fornecido para o `/uri:` parâmetro com o URI de sua instância do serviço de dados de exemplo Northwind.

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a>Para gerar classes c# baseadas no arquivo de modelo conceitual (CSDL)

- No prompt de comando, execute o seguinte comando sem quebras de linha:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a>Para gerar classes do Visual Basic com base no arquivo de modelo conceitual (CSDL)

- No prompt de comando, execute o seguinte comando sem quebras de linha:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a>Para gerar classes c# com base em arquivo. edmx

- No prompt de comando, execute o seguinte comando sem quebras de linha:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a>Para gerar classes do Visual Basic com base em arquivo. edmx

- No prompt de comando, execute o seguinte comando sem quebras de linha:

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a>Consulte também

- [Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md) (Gerando a biblioteca de clientes do serviço de dados)
- [Como: Adicionar uma referência de serviço de dados](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
- [Utilitário de cliente do WCF Data Service (DataSvcUtil.exe)](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)
