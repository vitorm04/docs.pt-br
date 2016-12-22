---
title: "Como criar grades de propriedades para configura&#231;&#245;es de usu&#225;rio no Visual Basic | Microsoft Docs"
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
  - "Objeto My.Settings, criando grades de propriedades para configurações do usuário"
  - "grades de propriedades"
  - "grades de propriedades, criando para configurações do usuário"
  - "configurações do usuário, criando grades de propriedades"
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como criar grades de propriedades para configura&#231;&#245;es de usu&#225;rio no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode criar uma grade de propriedades para Configurações de Usuário preenchendo um controle <xref:System.Windows.Forms.PropertyGrid> com as propriedades de configuração do usuário do objeto `My.Settings`.  
  
> [!NOTE]
>  Para que este exemplo funcione, seu aplicativo deve ter suas configurações de usuário configuradas.  Para obter mais informações, consulte [Gerenciando configurações de aplicativo \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet).  
  
 O objeto `My.Settings` expõe cada configuração como uma propriedade.  O nome da propriedade é o mesmo do nome da configuração, e o tipo da propriedade é o mesmo do tipo da configuração.  O **Scope** da configuração determina se a propriedade é somente leitura; a propriedade para uma configuração com escopo de **Application** é somente para leitura, enquanto a propriedade para uma configuração com escopo de **User** é de leitura e escrita.  Para obter mais informações, consulte [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Você não pode alterar ou salvar os valores das configurações com escopo de aplicativo em tempo de execução.  Configurações com escopo de aplicativo só podem ser alteradas ao criar o aplicativo \(através do **Project Designer**\) ou editando o arquivo de configuração do aplicativo.  Para obter mais informações, consulte [Gerenciando configurações de aplicativo \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet).  
  
 Este exemplo usa um controle <xref:System.Windows.Forms.PropertyGrid> para acessar as propriedades de configuração do usuário do objeto `My.Settings`.  Por padrão, o <xref:System.Windows.Forms.PropertyGrid> mostra todas as propriedades do objeto `My.Settings`.  No entanto, as propriedades de configuração de usuário têm o atributo <xref:System.Configuration.UserScopedSettingAttribute>.  Este exemplo define a propriedade <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> de <xref:System.Windows.Forms.PropertyGrid> como <xref:System.Configuration.UserScopedSettingAttribute> para exibir somente as propriedades de configuração de usuário.  
  
### Adicionar uma grade de propriedade de configuração  do usuário  
  
1.  Adicione o controle **PropertyGrid** da **Toolbox** para a superfície de design do seu aplicativo, assumido aqui como sendo   `Form1`.  
  
     O nome padrão do controle de grade de propriedade é `PropertyGrid1`.  
  
2.  Clique duas vezes na superfície de design para `Form1` abrir o código para o manipulador de eventos de carregar formulário.  
  
3.  Defina o objeto `My.Settings` como o objeto selecionado para a grade propriedade.  
  
     [!code-vb[VbVbalrMyResources#11](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_1.vb)]  
  
4.  Configure a grade propriedade para mostrar somente as configurações de usuário.  
  
     [!code-vb[VbVbalrMyResources#12](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_2.vb)]  
  
    > [!NOTE]
    >  Para mostrar somente as configurações de escopo do aplicativo, use o atributo de <xref:System.Configuration.ApplicationScopedSettingAttribute> em vez de <xref:System.Configuration.UserScopedSettingAttribute>.  
  
## Programação robusta  
 O aplicativo salva as configurações de usuário quando o aplicativo é desligado.  Para salvar as configurações imediatamente, chame o método `My.Settings.Save`.  Para obter mais informações, consulte [Como persistir configurações de usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## Consulte também  
 [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [Como ler configurações do aplicativo no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)   
 [Como alterar configurações do usuário no Visual Basic](../Topic/How%20to:%20Change%20User%20Settings%20in%20Visual%20Basic.md)   
 [Como persistir configurações de usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)   
 [Gerenciando configurações de aplicativo \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)