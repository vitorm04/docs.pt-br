---
title: Empacotando e implantando minhas extensões personalizadas
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: a2e2a6705fb3d8d4424d46d96bbf49b41e1414af
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330256"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a>Empacotar e implantar minhas extensões personalizadas (Visual Basic)

Visual Basic fornece uma maneira fácil de implantar suas extensões de namespace `My` personalizadas usando modelos do Visual Studio. Se você estiver criando um modelo de projeto para o `My` qual suas extensões são parte integrante do novo tipo de projeto, você pode apenas incluir `My` o código de extensão personalizado com o projeto ao exportar o modelo. Para obter mais informações sobre como exportar modelos de projeto, consulte [como: criar modelos de projeto](/visualstudio/ide/how-to-create-project-templates).

Se sua extensão `My` personalizada estiver em um único arquivo de código, você poderá exportar o arquivo como um modelo de item que os usuários podem adicionar a qualquer tipo de projeto de Visual Basic. Em seguida, você pode personalizar o modelo de item para habilitar recursos adicionais e comportamento `My` para sua extensão personalizada em um projeto Visual Basic. Esses recursos incluem o seguinte:

- Permitir que os usuários gerenciem `My` sua extensão personalizada na página **minhas extensões** do designer de projeto Visual Basic.

- Adicionar automaticamente sua extensão `My` personalizada quando uma referência a um assembly especificado é adicionada a um projeto.

- Ocultando `My` o modelo de item de extensão na caixa de diálogo **Adicionar item** para que ele não seja incluído na lista de itens de projeto.

Este tópico discute como empacotar uma extensão personalizada `My` como um modelo de item oculto que pode ser gerenciado na página **minhas extensões** do Designer de projeto do Visual Basic. A extensão `My` personalizada também pode ser adicionada automaticamente quando uma referência a um assembly especificado é adicionada a um projeto.

## <a name="create-a-my-namespace-extension"></a>Criar uma extensão de namespace My

A primeira etapa na criação de um pacote de implantação para `My` uma extensão personalizada é criar a extensão como um único arquivo de código. Para obter detalhes e orientações sobre como criar uma extensão `My` personalizada, consulte [estendendo o Namespace My no Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).

## <a name="export-a-my-namespace-extension-as-an-item-template"></a>Exportar uma extensão de namespace My como um modelo de item

Depois de ter um arquivo de código que inclui `My` sua extensão de namespace, você pode exportar o arquivo de código como um modelo de item do Visual Studio. Para obter instruções sobre como exportar um arquivo como um modelo de item do Visual Studio, consulte [como: criar modelos de item](/visualstudio/ide/how-to-create-item-templates).

> [!NOTE]
> Se a `My` extensão do namespace tiver uma dependência em um assembly específico, você poderá personalizar seu modelo de item para instalar `My` automaticamente a extensão do namespace quando uma referência a esse assembly for adicionada. Como resultado, você desejará excluir essa referência de assembly ao exportar o arquivo de código como um modelo de item do Visual Studio.

## <a name="customize-the-item-template"></a>Personalizar o modelo de item

Você pode habilitar o modelo de item a ser gerenciado na página **minhas extensões** do designer de projeto Visual Basic. Você também pode habilitar o modelo de item a ser adicionado automaticamente quando uma referência a um assembly especificado for adicionada a um projeto. Para habilitar essas personalizações, você adicionará um novo arquivo, chamado de arquivo CustomData, ao seu modelo e, em seguida, adicionará um novo elemento ao XML em seu arquivo. vstemplate.

### <a name="add-the-customdata-file"></a>Adicionar o arquivo CustomData

O arquivo CustomData é um arquivo de texto que tem uma extensão de nome de arquivo de. CustomData (o nome do arquivo pode ser definido como qualquer valor significativo para seu modelo) e que contém XML. O XML no arquivo CustomData instrui o Visual Basic a incluir sua `My` extensão quando os usuários usam a página **minhas extensões** do Designer de projeto do Visual Basic. Opcionalmente, você pode adicionar o `AssemblyFullName>` atributo <ao seu XML de arquivo CustomData. Isso instrui Visual Basic a instalar automaticamente sua extensão personalizada `My` quando uma referência a um determinado assembly for adicionada ao projeto. Você pode usar qualquer editor de texto ou editor de XML para criar o arquivo CustomData e, em seguida, adicioná-lo à pasta compactada do modelo de item (arquivo. zip).

Por exemplo, o XML a seguir mostra o conteúdo de um arquivo CustomData que adicionará o item de modelo à pasta minhas extensões de um projeto Visual Basic quando uma referência ao assembly Microsoft. VisualBasic. PowerPacks. vs. dll for adicionada ao projeto.

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

O arquivo CustomData contém um elemento `VBMyExtensionTemplate>` <que tem atributos, conforme listado na tabela a seguir.

|Atributo|Descrição|
|---|---|
|`ID`|Obrigatórios. Um identificador exclusivo para a extensão. Se a extensão que tem essa ID já tiver sido adicionada ao projeto, o usuário não será solicitado a adicioná-la novamente.|
|`Version`|Obrigatórios. Um número de versão para o modelo de item.|
|`AssemblyFullName`|Opcional. Um nome de assembly. Quando uma referência a esse assembly é adicionada ao projeto, o usuário será solicitado a adicionar a `My` extensão a partir deste modelo de item.|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>Adicione o \<elemento CustomDataSignature> ao arquivo. vstemplate

Para identificar o modelo de item do Visual Studio `My` como uma extensão de namespace, você também deve modificar o arquivo. vstemplate para seu modelo de item. Você deve adicionar um `<CustomDataSignature>` elemento ao `<TemplateData>` elemento. O `<CustomDataSignature>` elemento deve conter o texto `Microsoft.VisualBasic.MyExtension`, conforme mostrado no exemplo a seguir.

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

Você não pode modificar os arquivos em uma pasta compactada (arquivo. zip) diretamente. Você deve copiar o arquivo. vstemplate da pasta compactada, modificá-lo e, em seguida, substituir o arquivo. vstemplate na pasta compactada por sua cópia atualizada.

O exemplo a seguir mostra o conteúdo de um arquivo. vstemplate que tem `<CustomDataSignature>` o elemento adicionado.

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

Para instalar o modelo, você pode copiar a pasta compactada (arquivo *. zip* ) para a pasta Visual Basic item templates. Por padrão, os modelos de item de usuário estão localizados no *%USERPROFILE%\Documents\Visual Studio \<\>versão \Templates\ItemTemplates\Visual Basic*. Como alternativa, você pode publicar o modelo como um arquivo de Instalador do Visual Studio (*. VSI*).

## <a name="see-also"></a>Veja também

- [Estendendo o Meu Namespace no Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [Estendendo o modelo de aplicativo do Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [Como personalizar quais objetos estão disponíveis em My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Página Minhas extensões, Designer de projeto](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
