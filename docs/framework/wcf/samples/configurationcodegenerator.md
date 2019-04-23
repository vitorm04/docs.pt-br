---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: 97197926db0b44f1ad36e2eba6ab6bec42eced33
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773669"
---
# <a name="configurationcodegenerator"></a>ConfigurationCodeGenerator
O ConfigurationCodeGenerator é uma ferramenta que você pode usar para expor suas implementações de canal personalizado para o sistema de configuração. Isso permite que os usuários do seu canal personalizado configurar seu canal usando um arquivo. config exatamente como eles configuraria uma fornecida pelo sistema de associação, como `NetTcpBinding` ou um personalizado de associação usando o `TcpTransportBindingElement`.  
  
 Quando você escrever um canal personalizado e expô-lo para o modelo de programação usando uma nova `BindingElement` ou `Binding`, você deve criar um conjunto de classes para tornar o `BindingElement` ou `Binding` configurável usando um arquivo. config. Você pode usar a ferramenta ConfigurationCodeGenerator para gerar essas classes e aprimorar a experiência do cliente.  
  
### <a name="to-build-the-tool"></a>Para a ferramenta de compilação  
  
1. Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Compilando a solução gera um arquivo: ConfigurationCodeGenerator.exe. O arquivo SampleRun.cmd tem uma linha de comando de exemplo que mostra como usar essa ferramenta para gerar as classes para o [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo.  
  
### <a name="to-run-the-tool"></a>Para executar a ferramenta  
  
1. No prompt de comando, digite o seguinte se você tiver uma personalizadas `BindingElement` personalizado e tipo `Binding` tipo:  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     Ou digite o seguinte se você tiver apenas um personalizado `BindingElement` tipo:  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Ou digite o seguinte se você tiver apenas um personalizado `Binding` tipo:  
  
    ```  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     O comando gera três arquivos. cs para o `BindingElement` (se você tiver especificado a ser: opção), cinco arquivos. cs para o padrão `Binding` (se você tiver especificado o /sb: opção) e um arquivo. XML.  
  
    1.  Se você usou a opção /be, uma da. cs arquivos implementa o `BindingElementExtensionSection` para seu elemento de associação. Este código expõe seu `BindingElement` ao sistema de configuração, para que os outros ligações personalizadas podem usar o elemento de associação. Os outros arquivos têm classes que representam os padrões e constantes. Os arquivos têm `//TODO` comentários para lembrá-lo para atualizar os valores padrão.  
  
    2.  Se você especificou a opção /sb, dois dos arquivos. cs implementam uma `StandardBindingElement` e um `StandardBindingCollectionElement` respectivamente, que expõe a associação padrão para o sistema de configuração. Os outros arquivos têm classes que representam os padrões e constantes. Os arquivos têm `//TODO` comentários para lembrá-lo para atualizar os valores padrão.  
  
         Se você tiver especificado o /sb: opção de CodeToAddTo\<*YourStdBinding*>. cs tem código que você deve adicionar manualmente para a classe que implementa a associação padrão.  
  
     O arquivo de SampleConfig.xml contém o código de configuração que você deve adicionar ao arquivo de configuração que registra os manipuladores definidos na etapa anterior 1 ou 2.  
