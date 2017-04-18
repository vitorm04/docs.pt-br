---
title: Implantando aplicativos que referenciam controles de Power Packs (Visual Studio) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 4d342e655dcfe18ed3b5fc1d2710571ed8e3369e
ms.lasthandoff: 03/13/2017

---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a>Implantando aplicativos que referenciam controles de Power Packs (Visual Studio)
Se você deseja implantar um aplicativo que faz referência aos controles de Power Packs (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, ou <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), os controles devem ser instalados no computador de destino.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> </xref:Microsoft.VisualBasic.PowerPacks.OvalShape> </xref:Microsoft.VisualBasic.PowerPacks.LineShape>  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a>Instalação dos controles de Power Packs como um pré-requisito  
 Para implantar um aplicativo com êxito, você também deve implantar todos os componentes que são referenciados pelo aplicativo. O processo de instalação de componentes de pré-requisito é conhecido como *inicialização*.  
  
 Quando [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] está instalado no computador de desenvolvimento, um pacote de bootstrapper é adicionado de Power Packs o [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] directory bootstrapper. Este pacote estará disponível quando você seguir os procedimentos de adição de pré-requisitos para o [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] ou implantação do Windows Installer.  
  
 Por padrão, os componentes inicializados são implantados no mesmo local que o pacote de instalação. Como alternativa, você pode optar por implantar os componentes de um local de compartilhamento de arquivo ou URL da qual os usuários podem baixá-los conforme necessário.  
  
> [!NOTE]
>  Para instalar componentes inicializados, o usuário talvez precise de permissões de usuário administrativo ou semelhante no computador. Para [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] aplicativos, isso significa que o usuário deverá ter permissões administrativas para instalar o aplicativo, independentemente do nível de segurança especificado pelo aplicativo. Depois que o aplicativo é instalado, o usuário pode executar o aplicativo sem permissões administrativas.  
  
 Durante a instalação, os usuários deverá instalar os controles de Power Packs se não estiverem presentes no computador de destino.  
  
 Como alternativa para a inicialização, você pode implantar previamente os controles de Power Packs usando um sistema de distribuição eletrônica de software, como o Microsoft Systems Management Server.  
  
## <a name="see-also"></a>Consulte também  
 [Como instalar pré-requisitos com um aplicativo ClickOnce](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5)   
 [Controles do Visual Basic Power Packs](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)
