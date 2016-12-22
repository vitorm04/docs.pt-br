---
title: "Objeto My.Resources | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "My.Resources"
  - "My.Resources.MyResources.ResourceManager"
  - "My.Resources.MyResources.Culture"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Objeto My.Resources"
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Objeto My.Resources
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Fornece propriedades e classes para acessar recursos do aplicativo.  
  
## Comentários  
 O objeto `My.Resources` fornece acesso aos recursos do aplicativo e permite que você se recupere dinamicamente recursos para seu aplicativo.  Para obter mais informações, consulte [Gerenciando recursos de aplicativo \(.NET\)](/visual-studio/ide/managing-application-resources-dotnet).  
  
 O objeto `My.Resources` expõe apenas recursos globais.  Ele não fornece acesso aos arquivos de recursos associados a formulários.  Você deve acessar os recursos de formulário a partir do formulário.  Para obter mais informações, consulte [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/pt-br/9a96220d-a19b-4de0-9f48-01e5d82679e5).  
  
 Você pode acessar arquivos de recurso com cultura específica do aplicativo a partir do objeto `My.Resources`.  Por padrão, o `My.Resources` objeto procura de recursos que coincida com a cultura no arquivo de recurso a <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> propriedade.  No entanto, você pode substituir esse comportamento e especificar uma cultura específica para usar os recursos.  Para obter mais informações, consulte [Recursos em aplicativos de área de trabalho](../Topic/Resources%20in%20Desktop%20Apps.md).  
  
## Propriedades  
 As propriedades da `My.Resources` objeto fornecer acesso somente leitura para recursos de seu aplicativo.  Para adicionar ou remover recursos, use o **Project Designer**.  Para obter mais informações, consulte [Como: Adicionar ou remover recursos](http://msdn.microsoft.com/pt-br/7b77bc06-3952-4799-b029-def3f8f7f88d).  Você pode acessar recursos adicionados por meio do  **Project Designer**  usando `My.Resources.``resourceName`.  
  
 Você também pode adicionar ou remover os arquivos de recurso, selecionando o seu projeto no  **Gerenciador de Soluções**  e clicando em  **Adicionar Novo Item**  ou  **Adicionar Item Existente**  a partir do menu **Projeto**.  Você pode acessar recursos adicionados dessa maneira usando `My.Resources.``resourceFileName`. `resourceName`.  
  
 Cada recurso tem um nome, categoria e valor, e essas configurações de recurso determinam como a propriedade para acessar o recurso aparece no objeto `My.Resources`.  Para recursos adicionados na caixa  **Projeto Designer** :  
  
-   O nome determina o nome da propriedade,  
  
-   Os dados de recursos é o valor da propriedade,  
  
-   A categoria determina o tipo da propriedade:  
  
|||  
|-|-|  
|\<strong\>Categoria\<\/strong\>|Tipo de dados Propriedade|  
|**Sequências**|[String](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**Imagens**|<xref:System.Drawing.Bitmap>|  
|**Ícones**|<xref:System.Drawing.Icon>|  
|**Áudio**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> O <xref:System.IO.UnmanagedMemoryStream> classe deriva o <xref:System.IO.Stream> de classe, para que ele pode ser usado com métodos que recebem os fluxos, como o <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> método.|  
|**Files**|-   [Sequência de caracteres](../../../visual-basic/language-reference/data-types/string-data-type.md) para arquivos de texto.<br />-   <xref:System.Drawing.Bitmap> para arquivos de imagem.<br />-   <xref:System.Drawing.Icon> para arquivos ícone.<br />-   <xref:System.IO.UnmanagedMemoryStream> para arquivos de som.|  
|**Outros**|Determinado pela informação da coluna **Type** do designer.|  
  
## Classes  
 O objeto `My.Resources` expõe cada arquivo de recurso como uma classe com propriedades compartilhadas.  O nome da classe é o mesmo como o nome da arquivo de recurso.  Conforme descrito a seção anterior, os recursos em um arquivo de recurso são expostos como propriedades na classe.  
  
## Exemplo  
 Este exemplo define o título de um formulário para o recurso de seqüência de caracteres denominado `Form1Title` no arquivo de recurso do aplicativo.  Para o exemplo funcione, o aplicativo deve ter uma seqüência de caracteres denominada `Form1Title` em seu arquivo de recurso.  Para obter mais informações, consulte [Como: Adicionar ou remover recursos](http://msdn.microsoft.com/pt-br/7b77bc06-3952-4799-b029-def3f8f7f88d).  
  
 [!code-vb[VbVbalrMyResources#1](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]  
  
## Exemplo  
 Este exemplo define o ícone do formulário para o ícone chamado `Form1Icon`, que é  armazenado no arquivo de recurso do aplicativo.  Para o exemplo funcione, o aplicativo deve ter um ícone chamado `Form1Icon` em seu arquivo de recurso.  
  
 [!code-vb[VbVbalrMyResources#2](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]  
  
## Exemplo  
 Este exemplo define a imagem de plano de fundo de um formulário para o recurso de imagem nomeado `Form1Background`, que está no arquivo de recurso do aplicativo.  Para esse exemplo funcione, o aplicativo deve ter um recurso de imagem nomeado `Form1Background` em seu arquivo de recurso.  
  
 [!code-vb[VbVbalrMyResources#3](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]  
  
## Exemplo  
 Este exemplo reproduz o som que é armazenado como um recurso de áudio nomeado `Form1Greeting` no arquivo de recurso do aplicativo.  Para o exemplo funcione, o aplicativo deve ter um recurso de áudio nomeado `Form1Greeting` em seu arquivo de recurso.  O método `My.Computer.Audio.Play` está disponível apenas para aplicativos Windows Forms.  
  
 [!code-vb[VbVbalrMyResources#4](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]  
  
## Exemplo  
 Este exemplo recupera a versão de cultura francesa de um recurso de seqüência de caracteres do aplicativo.  O recurso é denominado `Message`.  Para alterar a cultura que o `My.Resources` usa o objeto, o exemplo usa <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.  
  
 Para esse exemplo funcione, o aplicativo deve ter uma seqüência de caracteres denominada `Message` em seu recurso de arquivo e o aplicativo devem ter a versão de cultura francesa desse arquivo de recurso, fr\-FR.  Para obter mais informações, consulte [Como: Adicionar ou remover recursos](http://msdn.microsoft.com/pt-br/7b77bc06-3952-4799-b029-def3f8f7f88d).  Se o aplicativo não tiver a versão de cultura francesa do arquivo de recurso, o `My.Resource` objeto recupera o recurso do arquivo de recurso de cultura padrão.  
  
 [!code-vb[VbVbalrMyResources#10](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]  
  
## Consulte também  
 [Como: Adicionar ou remover recursos](http://msdn.microsoft.com/pt-br/7b77bc06-3952-4799-b029-def3f8f7f88d)   
 [Gerenciando recursos de aplicativo \(.NET\)](/visual-studio/ide/managing-application-resources-dotnet)   
 [Recursos em aplicativos de área de trabalho](../Topic/Resources%20in%20Desktop%20Apps.md)   
 [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/pt-br/9a96220d-a19b-4de0-9f48-01e5d82679e5)