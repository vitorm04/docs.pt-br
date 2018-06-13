---
title: Implantando aplicativos que referenciam controles de Power Packs (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
ms.openlocfilehash: bd235bc0b4a7f9978333931ae1dce012c0950374
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587499"
---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a>Implantando aplicativos que referenciam controles de Power Packs (Visual Studio)
Se você deseja implantar um aplicativo que faz referência os controles de Power Packs (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, ou <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), os controles devem ser instalados no computador de destino.  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a>Instalando os controles de Power Packs como um pré-requisito  
 Para implantar um aplicativo, você também deve implantar todos os componentes que são referenciados pelo aplicativo. O processo de instalação de componentes de pré-requisito é conhecido como *inicializar*.  
  
 Quando o Visual Studio está instalado no computador de desenvolvimento, um pacote de bootstrapper Power Packs é adicionado ao diretório de bootstrapper do Visual Studio. Este pacote está disponível, em seguida, quando você seguir os procedimentos para adicionar pré-requisitos para o [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] ou implantação do Windows Installer.  
  
 Por padrão, inicializar componentes são implantados no mesmo local que o pacote de instalação. Como alternativa, você pode optar por implantar os componentes de um local de compartilhamento de arquivo ou URL da qual os usuários podem baixá-las conforme necessário.  
  
> [!NOTE]
>  Para instalar componentes inicializados, o usuário talvez precise de permissões de usuário administrativo ou semelhante no computador. Para [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplicativos, isso significa que o usuário deverá ter permissões administrativas para instalar o aplicativo, independentemente do nível de segurança especificado pelo aplicativo. Depois que o aplicativo é instalado, o usuário pode executar o aplicativo sem permissões administrativas.  
  
 Durante a instalação, os usuários serão solicitados a instalar os controles de Power Packs se eles não estiverem presentes no computador de destino.  
  
 Como alternativa para inicializar, você pode implantar previamente os controles de Power Packs usando um sistema de distribuição eletrônica de software, como o Microsoft Systems Management Server.  
  
## <a name="see-also"></a>Consulte também  
 [Como instalar pré-requisitos com um aplicativo ClickOnce](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [Controles de Power Packs do Visual Basic](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)
