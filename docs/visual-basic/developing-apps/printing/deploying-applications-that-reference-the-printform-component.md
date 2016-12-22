---
title: "Deploying Applications That Reference the PrintForm Component (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "PrintForm component [Visual Basic], deploying"
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Deploying Applications That Reference the PrintForm Component (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Se desejar implantar um aplicativo que faz referência a <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente, o componente deve ser instalado no computador de destino.  
  
 Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá\-los no [Centro de Download](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## Instalando o PrintForm como um pré\-requisito  
 Para implantar um aplicativo com êxito, você também deve implantar todos os componentes que são referenciados pelo aplicativo. O processo de instalação de componentes de pré\-requisito é conhecido como *inicialização*.  
  
 Quando o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente é instalado em seu computador de desenvolvimento, um pacote de bootstrapper do Microsoft Visual Basic Power Packs é adicionado para o [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] directory bootstrapper. Este pacote estará disponível quando você seguir os procedimentos de adição de pré\-requisitos para o [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] ou implantação do Windows Installer.  
  
 Por padrão, os componentes inicializados são implantados no mesmo local que o pacote de instalação. Como alternativa, você pode optar por implantar os componentes de um local de compartilhamento de arquivo ou URL da qual os usuários podem baixá\-los conforme necessário.  
  
> [!NOTE]
>  Para instalar componentes inicializados, o usuário talvez precise de permissões de usuário administrativo ou semelhante no computador. Para [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] aplicativos, isso significa que o usuário deverá ter permissões administrativas para instalar o aplicativo, independentemente do nível de segurança especificado pelo aplicativo. Depois que o aplicativo é instalado, o usuário pode executar o aplicativo sem permissões administrativas.  
  
 Durante a instalação, os usuários serão solicitados a instalar o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente se ele não está presente no computador de destino.  
  
 Como alternativa para a inicialização, você pode implantar previamente o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente usando um sistema de distribuição eletrônica de software como o Microsoft Systems Management Server.  
  
## Consulte também  
 [Como instalar pré\-requisitos com um aplicativo ClickOnce](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [Não na compilação: escolhendo uma estratégia de implantação](http://msdn.microsoft.com/pt-br/ecd632d8-063c-4028-b785-81bba045107b)   
 [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md)