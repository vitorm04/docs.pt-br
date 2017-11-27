---
title: "Empacotando e implantando personalizadas extensões do My (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94a9ea977d0add14ae9f0c9a889b008b94610ee0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="packaging-and-deploying-custom-my-extensions-visual-basic"></a>Empacotando e implantando personalizadas extensões do My (Visual Basic)
Visual Basic oferece uma maneira fácil para você implantar personalizados `My` extensões do namespace usando modelos do Visual Studio. Se você estiver criando um modelo de projeto para o qual o `My` extensões são uma parte integrante do novo tipo de projeto, você pode apenas incluir personalizados `My` código de extensão com o projeto quando você exportar o modelo. Para obter mais informações sobre como exportar modelos de projeto, consulte [como: criar modelos de projeto](/visualstudio/ide/how-to-create-project-templates).  
  
 Se seu personalizado `My` extensão está em um arquivo de código único, você pode exportar o arquivo como um modelo de item que os usuários podem adicionar a qualquer tipo de projeto do Visual Basic. Em seguida, você pode personalizar o modelo de item para habilitar recursos adicionais e o comportamento personalizados `My` extensão em um projeto do Visual Basic. Esses recursos incluem o seguinte:  
  
-   Permitir que os usuários gerenciem seu personalizado `My` extensão do **Minhas extensões** página do Designer de projeto do Visual Basic.  
  
-   Adicionando automaticamente personalizados `My` extensão quando uma referência a um assembly especificado é adicionada a um projeto.  
  
-   Ocultando o `My` modelo de item de extensão no **Adicionar Item** caixa de diálogo para que ele não está incluído na lista de itens de projeto.  
  
 Este tópico discute como empacotar um personalizado `My` extensão como um modelo de item oculto que pode ser gerenciado a partir de **Minhas extensões** página do Designer de projeto do Visual Basic. Personalizado `My` extensão também pode ser adicionada automaticamente quando uma referência a um assembly especificado é adicionada a um projeto.  
  
## <a name="create-a-my-namespace-extension"></a>Criar uma extensão do My namespace  
 A primeira etapa na criação de um pacote de implantação para um personalizado `My` extensão é criar a extensão como um arquivo de código único. Para obter detalhes e orientação sobre como criar um personalizado `My` extensão, consulte [estendendo o Namespace My no Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).  
  
## <a name="export-a-my-namespace-extension-as-an-item-template"></a>Exportar uma extensão do My namespace como um modelo de item  
 Depois que você tiver um arquivo de código que inclui seu `My` extensão do namespace, você pode exportar o arquivo de código como um modelo de item do Visual Studio. Para obter instruções sobre como exportar um arquivo como um modelo de item do Visual Studio, consulte [como: criar modelos de Item](/visualstudio/ide/how-to-create-item-templates).  
  
> [!NOTE]
>  Se seu `My` extensão do namespace tem uma dependência em um assembly específico, você pode personalizar o modelo de item para instalar automaticamente o `My` namespace extensão quando uma referência a esse assembly é adicionada. Como resultado, você deve excluir essa referência de assembly quando você exportar o arquivo de código como um modelo de item do Visual Studio.  
  
## <a name="customize-the-item-template"></a>Personalizar o modelo de item  
 Você pode habilitar o seu modelo de item a ser gerenciados a partir de **Minhas extensões** página do Designer de projeto do Visual Basic. Você também pode habilitar o modelo de item a ser adicionado automaticamente quando uma referência a um assembly especificado é adicionada a um projeto. Para habilitar essas personalizações, você irá adicionar um novo arquivo chamado arquivo CustomData, ao seu modelo e, em seguida, adicionar um novo elemento para o XML no arquivo. vstemplate.  
  
### <a name="add-the-customdata-file"></a>Adicione o arquivo CustomData  
 O arquivo CustomData é um arquivo de texto que tem uma extensão de nome de arquivo. CustomData (o nome do arquivo pode ser definido como qualquer valor significativo para o modelo) e que contém o XML. O XML no arquivo CustomData instrui o Visual Basic para incluir seu `My` extensão quando os usuários utilizarem o **Minhas extensões** página do Designer de projeto do Visual Basic. Opcionalmente, você pode adicionar o <`AssemblyFullName>` atributo ao seu arquivo XML CustomData. Isso instrui o Visual Basic para instalar automaticamente personalizados `My` extensão quando uma referência a um assembly específico é adicionada ao projeto. Você pode usar qualquer editor de texto ou editor XML para criar o arquivo CustomData e, em seguida, adicioná-lo à pasta compactada do seu modelo de item (arquivo. zip).  
  
 Por exemplo, o XML a seguir mostra o conteúdo de um arquivo CustomData que irá adicionar o item de modelo à pasta My Extensions de um projeto do Visual Basic quando uma referência ao assembly Microsoft.VisualBasic.PowerPacks.Vs.dll é adicionado ao projeto.  
  
```xml  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 O arquivo CustomData contém um <`VBMyExtensionTemplate>` elemento que tem atributos conforme listado na tabela a seguir.  
  
|Atributo|Descrição|  
|---|---|  
|`ID`|Necessário. Um identificador exclusivo para a extensão. Se a extensão que tem essa ID já foi adicionada ao projeto, o usuário não precisará adicioná-lo novamente.|  
|`Version`|Necessário. Um número de versão para o modelo de item.|  
|`AssemblyFullName`|Opcional. Um nome de assembly. Quando uma referência a esse assembly é adicionada ao projeto, o usuário será solicitado a adicionar o `My` extensão com base neste modelo de item.|  
  
### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>Adicionar o \<CustomDataSignature > elemento no arquivo. vstemplate  
 Para identificar o seu modelo de item do Visual Studio como um `My` extensão do namespace, você também deve modificar o arquivo. vstemplate para o modelo de item. Você deve adicionar um `<CustomDataSignature>` elemento para o `<TemplateData>` elemento. O `<CustomDataSignature>` elemento deve conter o texto `Microsoft.VisualBasic.MyExtension`, conforme mostrado no exemplo a seguir.  
  
```xml  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 Você não pode modificar diretamente os arquivos em uma pasta compactada (arquivo. zip). Você deve copiar o arquivo. vstemplate da pasta compactada, modificá-lo e, em seguida, substituir o arquivo. vstemplate na pasta compactada por sua cópia atualizada.  
  
 O exemplo a seguir mostra o conteúdo de um arquivo. vstemplate que tem o `<CustomDataSignature>` elemento adicionado.  
  
```xml  
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
  <TemplateData>  
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>  
    <Name>MyPrinterInfo</Name>  
    <Description>Custom My Extensions Item Template</Description>  
    <ProjectType>VisualBasic</ProjectType>  
    <SortOrder>10</SortOrder>  
    <Icon>__TemplateIcon.ico</Icon>  
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
  </TemplateData>  
  <TemplateContent>  
    <References />  
    <ProjectItem SubType="Code"   
                 TargetFileName="$fileinputname$.vb"  
                 ReplaceParameters="true"  
     >MyCustomExtensionModule.vb</ProjectItem>  
  </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="install-the-template"></a>Instalar o modelo  
 Para instalar o modelo, você pode copiar a pasta compactada (arquivo. zip) para a pasta de modelos de item Visual Basic (por exemplo, Meus Documentos\Visual Studio 2008\Templates\Item Templates\Visual Basic). Como alternativa, você pode publicar o modelo como um arquivo do instalador do Visual Studio (VSI).  
  
## <a name="see-also"></a>Consulte também  
 [Extensão do My Namespace no Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)  
 [Estendendo o modelo de aplicativo do Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)  
 [Personalizando quais objetos estão disponíveis em My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [Página Minhas extensões, Designer de projeto](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
