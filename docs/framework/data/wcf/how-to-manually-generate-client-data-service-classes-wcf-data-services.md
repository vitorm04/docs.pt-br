---
title: 'Como: gerar manualmente as Classes de serviço de dados do cliente (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: 24d19f10e025b765cfc7df73ba80d223fbfa8074
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358988"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a>Como: gerar manualmente as Classes de serviço de dados do cliente (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] integra-se com o Visual Studio para que você possa gerar classes de serviço de dados do cliente automaticamente quando você usa o **adicionar referência de serviço** caixa de diálogo para adicionar uma referência a um serviço de dados em um projeto do Visual Studio. Para obter mais informações, consulte [como: adicionar uma referência de serviço de dados](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md). Você pode gerar manualmente as mesmas classes de serviço de dados do cliente usando a ferramenta de geração de código, `DataSvcUtil.exe`. Essa ferramenta, que está incluída no [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], gera classes do .NET Framework da definição de serviço de dados. Ele também pode ser usado para gerar classes de serviço de dados do arquivo de modelo conceitual. (CSDL) e do arquivo. edmx que representa um modelo do Entity Framework em um projeto do Visual Studio.  
  
 O exemplo neste tópico cria classes de serviço de dados do cliente com base no serviço de dados de exemplo Northwind. Esse serviço é criado quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Alguns exemplos neste tópico exigem o arquivo de modelo conceitual para o modelo do Northwind. Para obter mais informações, consulte [como: Use EdmGen.exe para gerar o modelo e os arquivos de mapeamento](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md). Alguns exemplos neste tópico exigem o arquivo. edmx para o modelo do Northwind. Para obter mais informações, consulte [. edmx visão geral do arquivo](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4).  
  
### <a name="to-generate-c-classes-that-support-data-binding"></a>Para gerar classes c# que dão suporte a associação de dados  
  
-   No prompt de comando, execute o seguinte comando sem quebras de linha:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  Você deve substituir o valor fornecido para o `/uri:` parâmetro com o URI da sua instância do serviço de dados de exemplo Northwind.  
  
### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a>Para gerar classes do Visual Basic que oferecem suporte à associação de dados  
  
-   No prompt de comando, execute o seguinte comando sem quebras de linha:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  Você deve substituir o valor fornecido para o `/uri:` parâmetro com o URI da sua instância do serviço de dados de exemplo Northwind.  
  
### <a name="to-generate-c-classes-based-on-the-service-uri"></a>Para gerar classes c# com base no URI de serviço  
  
-   No prompt de comando, execute o seguinte comando sem quebras de linha:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  Você deve substituir o valor fornecido para o `/uri:` parâmetro com o URI da sua instância do serviço de dados de exemplo Northwind.  
  
### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a>Para gerar classes do Visual Basic com base no URI de serviço  
  
-   No prompt de comando, execute o seguinte comando sem quebras de linha:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  Você deve substituir o valor fornecido para o `/uri:` parâmetro com o URI da sua instância do serviço de dados de exemplo Northwind.  
  
### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a>Para gerar classes c# baseados no arquivo de modelo conceitual (CSDL)  
  
-   No prompt de comando, execute o seguinte comando sem quebras de linha:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs  
    ```  
  
### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a>Para gerar classes do Visual Basic com base no arquivo de modelo conceitual (CSDL)  
  
-   No prompt de comando, execute o seguinte comando sem quebras de linha:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb  
    ```  
  
### <a name="to-generate-c-classes-based-on-the-edmx-file"></a>Para gerar classes c# com base no arquivo. edmx  
  
-   No prompt de comando, execute o seguinte comando sem quebras de linha:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs   
    ```  
  
### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a>Para gerar classes do Visual Basic com base no arquivo. edmx  
  
-   No prompt de comando, execute o seguinte comando sem quebras de linha:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb   
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md) (Gerando a biblioteca de clientes do serviço de dados)  
 [Como adicionar uma referência de serviço de dados](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)  
 [Utilitário de cliente do WCF Data Service (DataSvcUtil.exe)](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)
