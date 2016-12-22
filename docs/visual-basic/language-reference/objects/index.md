---
title: "Objetos (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "objetos [Visual Basic]"
ms.assetid: 651c73e4-dca8-402b-9c6b-e3902b3a3f4b
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Objetos (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este tópico fornece links para outros tópicos desse documento, o tempo de execução Visual Basic objetos e contêm tabelas de seus procedimentos membros, propriedades e eventos.  
  
## Objetos de tempo de execução do Visual Basic  
  
|||  
|-|-|  
|<xref:Microsoft.VisualBasic.Collection>|Fornece uma maneira conveniente para ver um grupo de itens relacionado como um único objeto.|  
|<xref:Microsoft.VisualBasic.Information.Err%2A>|Contém informações sobre erros de tempo de execução.|  
|O `My.Application` objeto consiste de classes a seguir:<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>fornece membros que estão disponíveis em todos os projetos.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>fornece membros disponíveis em aplicativos Windows Forms.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>fornece membros disponíveis em aplicativos de console.|Fornece dados que está associados apenas com o aplicativo atual ou DLL.  Nenhuma informação de nível de sistema pode ser alterada com `My.Application`.<br /><br /> Alguns membros estão disponíveis somente para Formulários do Windows ou aplicativos do console.|  
|`My.Application.Info` \(<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Info%2A>\)|Fornece propriedades para obter informações sobre um aplicativo, como o número de versão, descrição, assemblies carregados e assim por diante.|  
|`My.Application.Log` \(<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>\)|Fornece uma propriedade e métodos para gravar informações de evento e de exceção aos ouvintes do log do aplicativo.|  
|`My.Computer` \(<xref:Microsoft.VisualBasic.Devices.Computer>\)|Fornece propriedades para manipular os componentes do computador, como áudio, o relógio, o teclado, o sistema de arquivos e assim por diante.|  
|`My.Computer.Audio` \(<xref:Microsoft.VisualBasic.Devices.Audio>\)|Fornece métodos para tocar sons.|  
|`My.Computer.Clipboard` \(<xref:Microsoft.VisualBasic.Devices.Computer.Clipboard%2A>\)|Fornece métodos para manipular a Área de transferência.|  
|`My.Computer.Clock` \(<xref:Microsoft.VisualBasic.Devices.Clock>\)|Fornece propriedades para acessar a hora local e o Universal Coordinated Time \(equivalente ao horário de Greenwich\) atuais do relógio do sistema.|  
|`My.Computer.FileSystem` \(<xref:Microsoft.VisualBasic.FileIO.FileSystem>\)|Proporciona propriedades e métodos para se trabalhar com discos, arquivos e diretórios.|  
|`My.Computer.FileSystem.SpecialDirectories` \(<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>\)|Fornece propriedades para acessar normalmente referenciada diretórios.|  
|`My.Computer.Info` \(<xref:Microsoft.VisualBasic.Devices.ComputerInfo>\)|Fornece propriedades para obter informações sobre a memória do computador, assemblys carregados, nome, e sistema operacional.|  
|`My.Computer.Keyboard` \(<xref:Microsoft.VisualBasic.Devices.Keyboard>\)|Fornece propriedades para acessar o estado atual do teclado, como quais teclas estão pressionadas no momento, e fornece um método para enviar pressionamentos de teclas para a janela ativa.|  
|`My.Computer.Mouse` \(<xref:Microsoft.VisualBasic.Devices.Mouse>\)|Fornece propriedades para obter informações sobre o formato e a configuração do mouse instalado no computador local.|  
|`My.Computer.Network` \(<xref:Microsoft.VisualBasic.Devices.Network>\)|Fornece métodos para interação com a rede à qual o computador está conectado, um evento e uma propriedade.|  
|`My.Computer.Ports` \(<xref:Microsoft.VisualBasic.Devices.Ports>\)|Fornece uma propriedade e um método para acessar portas seriais do computador.|  
|`My.Computer.Registry` \(<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>\)|Fornece propriedades e métodos para manipular o registro.|  
|[Objeto My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)|Fornece propriedades para acessar uma instância de cada Windows Form declarado no projeto atual.|  
|`My.Log` \(<xref:Microsoft.VisualBasic.Logging.AspLog>\)|Fornece uma propriedade e métodos para gravar informações de evento e de exceção para ouvintes de log do aplicativo para aplicativos da Web.|  
|[Objeto My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)|Obtém o objeto <xref:System.Web.HttpRequest> para a página solicitada.  O objeto `My.Request` contém informações sobre o solicitação HTTP atual.<br /><br /> O `My.Request` o objeto está disponível somente para [!INCLUDE[vstecasp](../../../visual-basic/developing-apps/programming/drives-directories-files/includes/vstecasp_md.md)] aplicativos.|  
|[Objeto My.Resources](../../../visual-basic/language-reference/objects/my-resources-object.md)|Fornece classes e propriedades para acessar recursos do aplicativo.|  
|[Objeto My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)|Obtém o <xref:System.Web.HttpResponse> objeto associado com o <xref:System.Web.UI.Page>.  Este objeto permite que você envie dados de resposta HTTP para um cliente e contém informações sobre essa resposta.<br /><br /> O `My.Response` o objeto está disponível somente para [!INCLUDE[vstecasp](../../../visual-basic/developing-apps/programming/drives-directories-files/includes/vstecasp_md.md)] aplicativos.|  
|[Objeto My.Settings](../../../visual-basic/language-reference/objects/my-settings-object.md)|Fornece propriedades e métodos para acessar as configurações do aplicativo.|  
|`My.User` \(<xref:Microsoft.VisualBasic.ApplicationServices.User>\)|Fornece acesso a informações sobre o usuário atual.|  
|[Objeto My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)|Fornece propriedades para criar e acessar uma única instância de cada serviço da Web que é referenciado pelo projeto atual.|  
|<xref:Microsoft.VisualBasic.FileIO.TextFieldParser>|Fornece métodos e propriedades para analisar texto estruturado arquivos.|  
  
## Consulte também  
 [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md)   
 [Visual Basic](../../../visual-basic/index.md)