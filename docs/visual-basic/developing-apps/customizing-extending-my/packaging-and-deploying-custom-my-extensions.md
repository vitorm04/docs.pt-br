---
title: "Empacotando e implantando Minhas extensões (Visual Basic) de personalizadas | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My namespace, customizing
- My namespace
- My namespace, extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 950592c0fb197959ce1c3cf6128093846a022709
ms.lasthandoff: 03/13/2017

---
# <a name="packaging-and-deploying-custom-my-extensions-visual-basic"></a>Empacotando e implantando personalizadas extensões My (Visual Basic)
Visual Basic fornece uma maneira fácil para você implantar seu personalizado `My` extensões do namespace usando modelos do Visual Studio. Se você estiver criando um modelo de projeto para o qual o `My` extensões são parte integrante do novo tipo de projeto, você pode apenas incluir seu personalizado `My` código de extensão com o projeto quando você exporta o modelo. Para obter mais informações sobre como exportar modelos de projeto, consulte [como: criar modelos de projeto](http://msdn.microsoft.com/library/a1a6999d-a34c-48a8-b1cf-027eb5c76398).  
  
 Se seu personalizado `My` extensão está em um arquivo de código único, você pode exportar o arquivo como um modelo de item que os usuários podem adicionar a qualquer tipo de projeto do Visual Basic. Em seguida, você pode personalizar o modelo de item para habilitar recursos adicionais e comportamentos para seu personalizado `My` extensão em um projeto do Visual Basic. Esses recursos incluem o seguinte:  
  
-   Permitindo que os usuários gerenciem seu personalizado `My` extensão o **extensões My** página do Designer de projeto do Visual Basic.  
  
-   Adicionando automaticamente seu personalizado `My` extensão quando uma referência a um assembly especificado é adicionada a um projeto.  
  
-   Ocultando o `My` modelo de item de extensão no **Adicionar Item** caixa de diálogo para que ele não está incluído na lista de itens de projeto.  
  
 Este tópico discute como empacotar um personalizado `My` extensão como um modelo de item oculto que possa ser gerenciado a **extensões My** página do Designer de projeto do Visual Basic. Personalizado `My` extensão também pode ser adicionada automaticamente quando uma referência a um assembly especificado é adicionada a um projeto.  
  
## <a name="create-a-my-namespace-extension"></a>Criar uma extensão My namespace  
 A primeira etapa na criação de um pacote de implantação para um personalizado `My` extensão é criar a extensão como um arquivo único de código. Para obter detalhes e orientação sobre como criar um personalizado `My` extensão, consulte [estendendo o Namespace My no Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).  
  
## <a name="export-a-my-namespace-extension-as-an-item-template"></a>Exportar uma extensão My namespace como um modelo de item  
 Depois de ter um arquivo de código que inclui seu `My` extensão do namespace, você pode exportar o arquivo de código como um modelo de item do Visual Studio. Para obter instruções sobre como exportar um arquivo como um modelo de item do Visual Studio, consulte [como: criar modelos de Item](http://msdn.microsoft.com/library/77bc53d4-d607-4820-a032-7e3b365891b5).  
  
> [!NOTE]
>  Se seu `My` extensão do namespace tem uma dependência em um assembly específico, você pode personalizar o modelo de item para instalar automaticamente o `My` quando uma referência a esse assembly for adicionada a extensão do namespace. Como resultado, você deve excluir essa referência de assembly quando você exportar o arquivo de código como um modelo de item do Visual Studio.  
  
## <a name="customize-the-item-template"></a>Personalizar o modelo de item  
 Você pode habilitar o seu modelo de item a ser gerenciado a partir de **extensões My** página do Designer de projeto do Visual Basic. Você também pode habilitar o modelo de item a ser adicionado automaticamente quando uma referência a um assembly especificado é adicionada a um projeto. Para habilitar essas personalizações, você irá adicionar um novo arquivo, chamado arquivo CustomData, ao seu modelo e, em seguida, adicione um novo elemento para o XML no arquivo. vstemplate.  
  
### <a name="add-the-customdata-file"></a>Adicionar o arquivo CustomData  
 O arquivo CustomData é um arquivo de texto que tem uma extensão de nome de arquivo. CustomData (o nome do arquivo pode ser definido como qualquer valor significativo para seu modelo) e que contém XML. O XML no arquivo CustomData instrui o Visual Basic para incluir sua `My` extensão quando os usuários utilizarem o **extensões My** página do Designer de projeto do Visual Basic. Opcionalmente, você pode adicionar o `AssemblyFullName>` atributo ao seu arquivo XML CustomData. Isso instrui o Visual Basic para instalar automaticamente seu personalizado `My` extensão quando uma referência a um assembly específico é adicionada ao projeto. Você pode usar qualquer editor de texto ou editor XML para criar o arquivo CustomData e, em seguida, adicioná-lo à pasta compactada do seu modelo de item (arquivo. zip).  
  
 Por exemplo, o XML a seguir mostra o conteúdo de um arquivo CustomData que irá adicionar o item de modelo à pasta My Extensions de um projeto do Visual Basic quando uma referência ao assembly Microsoft.VisualBasic.PowerPacks.Vs.dll é adicionado ao projeto.  
  
```  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 O arquivo CustomData contém um `VBMyExtensionTemplate>` elemento que tenha atributos conforme listado na tabela a seguir.  
  
|Atributo|Descrição|  
|---|---|  
|`ID`|Necessário. Um identificador exclusivo para a extensão. Se a extensão que tiver essa identificação já foi adicionada ao projeto, o usuário não precisará adicioná-lo novamente.|  
|`Version`|Necessário. Um número de versão do modelo de item.|  
|`AssemblyFullName`|Opcional. Um nome de assembly. Quando uma referência a esse assembly é adicionada ao projeto, o usuário será solicitado a adicionar o `My` extensão este modelo de item.|  
  
### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>Adicionar o \<CustomDataSignature > elemento para o arquivo. vstemplate  
 Para identificar o seu modelo de item do Visual Studio como um `My` extensão do namespace, você também deve modificar o arquivo. vstemplate para o modelo de item. Você deve adicionar uma `<CustomDataSignature>` elemento para o `<TemplateData>` elemento. O `<CustomDataSignature>` elemento deve conter o texto `Microsoft.VisualBasic.MyExtension`, conforme mostrado no exemplo a seguir.  
  
```  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 Você não pode modificar diretamente os arquivos em uma pasta compactada (arquivo. zip). Você deve copiar o arquivo. vstemplate da pasta compactada, modificá-lo e, em seguida, substitua o arquivo. vstemplate na pasta compactada por sua cópia atualizada.  
  
 O exemplo a seguir mostra o conteúdo de um arquivo. vstemplate que tem o `<CustomDataSignature>` elemento adicionado.  
  
```  
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
 Para instalar o modelo, você pode copiar a pasta compactada (arquivo. zip) para a pasta de modelos de item de Visual Basic (por exemplo, Meus Documentos\Visual Studio 2008\Templates\Item Templates\Visual Basic). Como alternativa, você pode publicar o modelo como um arquivo de instalação do Visual Studio (VSI).  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo o Meu Namespace no Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)   
 [Estendendo o modelo de aplicativo do Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)   
 [Personalizando quais objetos estão disponíveis em meu](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [Página Minhas extensões, Designer de projeto](https://docs.microsoft.com/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
