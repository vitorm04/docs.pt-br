---
title: "Empacotando e implantando minhas extens&#245;es personalizadas (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Meu namespace"
  - "Meu namespace, personalizando"
  - "Meu namespace, estendendo"
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Empacotando e implantando minhas extens&#245;es personalizadas (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Visual Basic oferece uma maneira fácil para você implantar as suas extensões de namespace `My` personalizadas usando modelos do Visual Studio.  Se você estiver criando um modelo de projeto para o qual as  extensões `My` são uma parte integrante de tipo de projeto de novo, você pode apenas incluir seu código personalizado de extensão `My` com o projeto  quando você exportar o modelo.  Para obter mais informações sobre como exportar modelos de projeto, consulte [Como criar modelos de projeto](../Topic/How%20to:%20Create%20Project%20Templates.md).  
  
 Se sua extensão `My` personalizada estiver em um arquivo único de código, você pode exportar o arquivo como um modelo de item que os usuários podem adicionar a qualquer tipo de projeto do Visual Basic.  Em seguida, você pode personalizar o modelo de item para habilitar recursos adicionais e comportamentos para a sua extensão `My` personalizada em um projeto Visual Basic.  Esses recursos incluem o seguinte:  
  
-   Permitindo que os usuários gerenciar sua extensão `My` personalizado a partir da página **My Extensions** do Designer de Projeto do Visual Basic.  
  
-   Adicionando a extensão `My` personalizada automaticamente quando uma referência a um assembly especificado é adicionada a um projeto.  
  
-   Ocultando o modelo de item de extensão `My` na caixa caixa de diálogo **Add Item** para que ele não seja incluído na lista de itens de projeto.  
  
 Este tópico discute como empacotar uma extensão `My` personalizada como um modelo de item oculto que pode ser gerenciado da página **My Extensions** do Visual Basic Project Designer.  A extensão `My` personalizada também pode ser adicionada automaticamente quando uma referência a um assembly especificado é adicionado a um projeto.  
  
## Criar uma extensão de My Namespace  
 A primeira etapa na criação um pacote de implantação de uma extensão `My` personalizada é criar a extensão como um arquivo único de código.  Para obter detalhes e orientação sobre como criar uma extensão `My` personalizada, consulte [Estendendo o namespace My no Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).  
  
## Exporta uma extensão de My Namespace como um modelo do item  
 Depois de ter um arquivo de código que inclui a sua extensão de `My` namespace, você pode exportar o arquivo de código como um modelo de item do Visual Studio.  Para obter instruções sobre como exportar um arquivo como um modelo de item do Visual Studio, consulte [Como criar modelos de item](../Topic/How%20to:%20Create%20Item%20Templates.md).  
  
> [!NOTE]
>  Se sua extensão de namespace `My` tiver uma dependência em um assembly específico, você pode personalizar o modelo de item para instalar automaticamente a extensão de namespace `My` quando uma referência a esse assembly for adicionada.  Como resultado, você vai querer excluir essa referência de assembly quando você exportar o arquivo de código como um modelo de item do Visual Studio.  
  
## Personaliza o modelo de item  
 Você pode habilitar o seu modelo de item a serem gerenciado da página **My Extensions** do Visual Basic Project Designer.  Você também pode habilitar o modelo de item a ser adicionado automaticamente quando uma referência a um conjunto especificado é adicionada a um projeto.  Para habilitar essas personalizações, você adicionará um novo arquivo, chamado arquivo CustomData, ao seu modelo e em seguida, adicionar um novo elemento para o XML no seu arquivo .vstemplate.  
  
### Adicionar o arquivo CustomData  
 O arquivo CustomData é um arquivo de texto que tem uma extensão de nome de arquivo de .CustomData \(o nome de arquivo pode ser definido como qualquer valor com significativo para o seu modelo\) e que contém XML.  O XML no arquivo CustomData instrui o Visual Basic para incluir sua extensão `My` quando os usuários usam a página  **My Extensions** do Visual Basic Project Designer.  Você pode opcionalmente adicionar o atributo \<`AssemblyFullName>` ao seu arquivo XML CustomData.  Isso instrui o Visual Basic para instalar automaticamente sua extensão `My` personalizada quando uma referência a um assembly específico é adicionada ao projeto.  Você pode usar qualquer editor de texto ou Editor XML para criar o arquivo CustomData, e então adicione\-la para a pasta compactada do seu modelo de item \(arquivo .zip\).  
  
 Por exemplo, o XML a seguir mostra o conteúdo de um arquivo CustomData que irá adicionar o item de modelo à pasta My Extensions de um projeto do Visual Basic quando uma referência ao Microsoft.VisualBasic.PowerPacks.Vs.dll for adicionado ao projeto.  
  
```  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 O arquivo CustomData contém um elemento \<`VBMyExtensionTemplate>` que tenha atributos conforme listado na tabela a seguir.  
  
|||  
|-|-|  
|Atributo|Descrição|  
|`ID`|Obrigatório.  Um identificador exclusivo para a extensão.  Se a extensão que tiver essa identificação já terá sido adicionada ao projeto, o usuário não precisará adicioná\-lo novamente.|  
|`Version`|Obrigatório.  Um número de versão para o modelo de item.|  
|`AssemblyFullName`|Opcional.  Um nome do assembly  Quando uma referência a esse assembly for adicionada ao projeto, o usuário precisará adicionar a extensão `My` para este modelo de item.|  
  
### Adicionar o elemento \<CustomDataSignature\> ao arquivo .vstemplate  
 Para identificar o seu modelo de item Visual Studio como uma extensão de namespace `My`,você deve também modificar o arquivo .vstemplate para o seu modelo de item.  Você deve adicionar um elemento `<CustomDataSignature>` para o elemento `<TemplateData>`.  O elemento `<CustomDataSignature>` deve conter o texto `Microsoft.VisualBasic.MyExtension`, conforme mostrado no exemplo o seguir.  
  
```  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 Você não pode modificar os arquivos em uma pasta compactada \(arquivo .zip\) diretamente.  Você deve copiar o arquivo .vstemplate a partir da pasta compactada, modificá\-lo e em seguida, substituir o arquivo .vstemplate na pasta compactada por sua cópia atualizada.  
  
 O exemplo a seguir mostra o conteúdo de um arquivo .vstemplate que tem o elemento `<CustomDataSignature>` adicionado.  
  
```  
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
  <TemplateData>  
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>  
    <Name>MyPrinterInfo</Name>  
    <Description>Custom My Extensions Item Template</Description>  
    <ProjectType>VisualBasic</ProjectType>  
    <SortOrder>10</SortOrder>  
    <Icon>__TemplateIcon.ico</Icon>  
    <CustomDataSignature       >Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
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
  
## Instalar o Modelo  
 Para instalar o modelo, você pode copiar a pasta compactada \(arquivo .zip\) para a pasta modelos de itens do Visual Basic \(por exemplo, My Documents\\Visual Studio 2008\\Templates\\Item Templates\\Visual Basic\).  Como alternativa, você pode publicar o modelo como um arquivo de Visual Studio Installer \(.vsi\).  Para obter informações sobre como publicar seu modelo como um arquivo Visual Studio Installer, consulte [NIB: How to: Publish Project Templates](http://msdn.microsoft.com/pt-br/b9087f58-64e9-4767-bf54-e3bf40d63b20).  
  
## Consulte também  
 [Estendendo o namespace My no Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)   
 [Estendendo o modelo de aplicativo do Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)   
 [Personalizando quais objetos estão disponíveis em My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [Página Minhas Extensões, Designer de Projeto](/visual-studio/ide/reference/my-extensions-page-project-designer-visual-basic)