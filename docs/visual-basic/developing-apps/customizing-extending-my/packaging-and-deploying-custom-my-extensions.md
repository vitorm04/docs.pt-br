---
title: Empacotando e implantando personalizadas extensões My (Visual Basic)
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 4212f58c39f63be6ba20c3b79e5d9c98d0615c5e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43487150"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a>Empacotar e implantar personalizado extensões My (Visual Basic)

Visual Basic fornece uma maneira fácil para você implantar o personalizado `My` extensões do namespace usando modelos do Visual Studio. Se você estiver criando um modelo de projeto para o qual sua `My` extensões são parte integrante do novo tipo de projeto, você pode apenas incluir seu personalizado `My` código de extensão com o projeto quando você exporta o modelo. Para obter mais informações sobre como exportar modelos de projeto, consulte [como: criar modelos de projeto](/visualstudio/ide/how-to-create-project-templates).

Se seu personalizado `My` extensão está em um arquivo de código único, você pode exportar o arquivo como um modelo de item que os usuários podem adicionar a qualquer tipo de projeto do Visual Basic. Em seguida, você pode personalizar o modelo de item para habilitar recursos adicionais e o comportamento para o personalizado `My` extensão em um projeto do Visual Basic. Esses recursos incluem o seguinte:

- Permitindo que os usuários gerenciem seu personalizado `My` extensão do **Minhas extensões** página do Designer de projeto do Visual Basic.

- Adicionando automaticamente seu personalizado `My` extensão quando uma referência a um assembly especificado é adicionada a um projeto.

- Ocultando o `My` modelo de item de extensão na **Add Item** caixa de diálogo para que ele não está incluído na lista de itens de projeto.

Este tópico discute como empacotar um personalizado `My` extensão como um modelo de item oculto que pode ser gerenciado do **Minhas extensões** página do Designer de projeto do Visual Basic. Personalizado `My` extensão também pode ser adicionada automaticamente quando uma referência a um assembly especificado é adicionada a um projeto.

## <a name="create-a-my-namespace-extension"></a>Criar uma extensão My namespace

A primeira etapa na criação de um pacote de implantação personalizado `My` extensão é criar a extensão como um arquivo de código único. Para obter detalhes e orientações sobre como criar um personalizado `My` extensão, consulte [estendendo o Namespace My no Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).

## <a name="export-a-my-namespace-extension-as-an-item-template"></a>Exportar uma extensão My namespace como um modelo de item

Depois que você tiver um arquivo de código que inclui seu `My` extensão do namespace, você pode exportar o arquivo de código como um modelo de item do Visual Studio. Para obter instruções sobre como exportar um arquivo como um modelo de item do Visual Studio, consulte [como: criar modelos de Item](/visualstudio/ide/how-to-create-item-templates).

> [!NOTE]
> Se sua `My` extensão do namespace tem uma dependência em um assembly específico, você pode personalizar seu modelo de item para instalar automaticamente seu `My` quando uma referência a esse assembly é adicionada a extensão do namespace. Como resultado, você desejará excluir essa referência de assembly quando você exportar o arquivo de código como um modelo de item do Visual Studio.

## <a name="customize-the-item-template"></a>Personalizar o modelo de item

Você pode habilitar o seu modelo de item a ser gerenciados a partir de **Minhas extensões** página do Designer de projeto do Visual Basic. Você também pode habilitar o modelo de item a ser adicionado automaticamente quando uma referência a um assembly especificado é adicionada a um projeto. Para habilitar essas personalizações, você irá adicionar um novo arquivo chamado arquivo CustomData, ao seu modelo e, em seguida, adicione um novo elemento ao XML em seu arquivo. vstemplate.

### <a name="add-the-customdata-file"></a>Adicione o arquivo CustomData

O arquivo CustomData é um arquivo de texto que tem uma extensão de nome de arquivo. CustomData (o nome do arquivo pode ser definido como qualquer valor significativo ao seu modelo) e que contém XML. O XML no arquivo CustomData instrui o Visual Basic para incluir sua `My` extensão quando os usuários usam o **Minhas extensões** página do Designer de projeto do Visual Basic. Opcionalmente, você pode adicionar o <`AssemblyFullName>` de atributo para o seu arquivo XML CustomData. Isso instrui o Visual Basic para instalar automaticamente seu personalizado `My` quando uma referência a um assembly específico de extensão é adicionada ao projeto. Você pode usar qualquer editor de texto ou editor XML para criar o arquivo CustomData e, em seguida, adicioná-lo para a pasta compactada do seu modelo item (arquivo. zip).

Por exemplo, o XML a seguir mostra o conteúdo de um arquivo CustomData que irá adicionar o item de modelo para a pasta Minhas extensões de um projeto do Visual Basic quando uma referência ao assembly Microsoft.VisualBasic.PowerPacks.Vs.dll é adicionado ao projeto.

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

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>Adicionar o \<CustomDataSignature > elemento para o arquivo. vstemplate

Para identificar o modelo de item do Visual Studio como um `My` extensão do namespace, você também deve modificar o arquivo. vstemplate para o modelo de item. Você deve adicionar uma `<CustomDataSignature>` elemento para o `<TemplateData>` elemento. O `<CustomDataSignature>` elemento deve conter o texto `Microsoft.VisualBasic.MyExtension`, conforme mostrado no exemplo a seguir.

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

Você não pode modificar diretamente os arquivos em uma pasta compactada (arquivo. zip). Você deve copiar o arquivo. vstemplate da pasta compactada, modificá-lo e, em seguida, substitua o arquivo. vstemplate na pasta compactada com a cópia atualizada.

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

Para instalar o modelo, você pode copiar a pasta compactada (*. zip* arquivo) para a pasta de modelos de item do Visual Basic. Por padrão, os modelos de item de usuário estão localizados na *%USERPROFILE%\Documents\Visual Studio \<versão\>\Templates\ItemTemplates\Visual Basic*. Como alternativa, você pode publicar o modelo como um instalador do Visual Studio (*vsi*) arquivos.

## <a name="see-also"></a>Consulte também

- [Estendendo o Meu Namespace em Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [Estendendo o modelo de aplicativo do Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [Personalizando quais objetos estão disponíveis em My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Página Minhas extensões, Designer de Projeto](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
