---
title: Implantando aplicativos que referenciam controles de Power Packs (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
ms.openlocfilehash: 3fd46a6e8aad61d2f8ce5a230c856470f913d0bd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551768"
---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a>Implantando aplicativos que referenciam controles de Power Packs (Visual Studio)
Se você deseja implantar um aplicativo que faz referência aos controles de Power Packs (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, ou <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), os controles devem ser instalados no computador de destino.  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a>Instalando os controles de Power Packs como um pré-requisito  
 Para implantar um aplicativo com êxito, você também deve implantar todos os componentes que são referenciados pelo aplicativo. O processo de instalação de componentes de pré-requisito é conhecido como *inicialização*.  
  
 Quando o Visual Studio está instalado no computador de desenvolvimento, um pacote de bootstrapper Power Packs é adicionado ao diretório de bootstrapper do Visual Studio. Este pacote está disponível, em seguida, quando você seguir os procedimentos de adição de pré-requisitos para qualquer um [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] ou implantação do Windows Installer.  
  
 Por padrão, os componentes inicializados são implantados no mesmo local do pacote de instalação. Como alternativa, você pode optar por implantar os componentes de um local de compartilhamento de arquivo ou URL da qual os usuários podem baixá-los conforme necessário.  
  
> [!NOTE]
>  Para instalar os componentes inicializados, o usuário talvez precise de permissões de usuário administrativo ou semelhante no computador. Para [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplicativos, isso significa que o usuário precisará de permissões administrativas para instalar o aplicativo, independentemente do nível de segurança especificado pelo aplicativo. Depois que o aplicativo é instalado, o usuário pode executar o aplicativo sem permissões administrativas.  
  
 Durante a instalação, os usuários deverão instalar os controles de Power Packs se eles não estiverem presentes no computador de destino.  
  
 Como alternativa para a inicialização, você pode implantar previamente os controles de Power Packs usando um sistema de distribuição eletrônica de software, como o Microsoft Systems Management Server.  
  
## <a name="see-also"></a>Consulte também
- [Como: Instalar pré-requisitos com um aplicativo ClickOnce](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)
- [Controles do Visual Basic Power Packs](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)
