---
title: 'Como: usar Svcutil.exe para validar o código de serviço compilado'
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: 599f5624b7eb0c32cbcc0a78e6c7f989ce470b58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038747"
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a>Como: usar Svcutil.exe para validar o código de serviço compilado
Você pode usar o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para detectar erros em implementações de serviço e as configurações sem hospedar o serviço.  
  
### <a name="to-validate-a-service"></a>Para validar um serviço  
  
1. Compile seu serviço em um arquivo executável e um ou mais assemblies dependentes.  
  
2. Abra um prompt de comando do SDK  
  
3. No prompt de comando, inicie a ferramenta Svcutil.exe usando o seguinte formato. Para obter mais informações sobre os vários parâmetros, consulte Validationsection o serviço do [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tópico.  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     Você deve usar o `/serviceName` opção para indicar o nome da configuração do serviço que você deseja validar.  
  
     O `assemblyPath` argumento especifica o caminho para o arquivo executável para o serviço e um ou mais assemblies que contêm os tipos de serviço a ser validado. O assembly executável deve ter um arquivo de configuração associado para fornecer a configuração do serviço. Você pode usar curingas padrão de linha de comando para fornecer vários assemblies.  
  
## <a name="example"></a>Exemplo  
 O comando a seguir o myServiceName serviço implementado no arquivo executável myServiceHost.exe.  O arquivo de configuração para o serviço (myServiceHost.exe.config) é carregado automaticamente.  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a>Consulte também

- [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
