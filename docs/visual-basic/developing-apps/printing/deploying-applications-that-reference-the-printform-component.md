---
title: Implantando aplicativos que referenciam o componente PrintForm (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
ms.openlocfilehash: 3dd7c348c4dc36a7ff64e76a93c05ddb24837079
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a>Implantando aplicativos que referenciam o componente PrintForm (Visual Basic)
Se você deseja implantar um aplicativo que faz referência a <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente, o componente deve ser instalado no computador de destino.  
  
 Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá-los no [Centro de Download](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## <a name="installing-the-printform-as-a-prerequisite"></a>Instalando o PrintForm como um pré-requisito  
 Para implantar um aplicativo, você também deve implantar todos os componentes que são referenciados pelo aplicativo. O processo de instalação de componentes de pré-requisito é conhecido como *inicializar*.  
  
 Quando o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente está instalado no computador de desenvolvimento, um pacote de bootstrapper do Microsoft Visual Basic Power Packs é adicionado ao diretório de bootstrapper do Visual Studio. Este pacote está disponível, em seguida, quando você seguir os procedimentos para adicionar pré-requisitos para o [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] ou implantação do Windows Installer.  
  
 Por padrão, inicializar componentes são implantados no mesmo local que o pacote de instalação. Como alternativa, você pode optar por implantar os componentes de um local de compartilhamento de arquivo ou URL da qual os usuários podem baixá-las conforme necessário.  
  
> [!NOTE]
>  Para instalar componentes inicializados, o usuário talvez precise de permissões de usuário administrativo ou semelhante no computador. Para [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplicativos, isso significa que o usuário deverá ter permissões administrativas para instalar o aplicativo, independentemente do nível de segurança especificado pelo aplicativo. Depois que o aplicativo é instalado, o usuário pode executar o aplicativo sem permissões administrativas.  
  
 Durante a instalação, os usuários serão solicitados a instalar o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente se ele não está presente no computador de destino.  
  
 Como alternativa para inicializar, você pode implantar previamente o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente por meio de um sistema de distribuição eletrônica de software como o Microsoft Systems Management Server.  
  
## <a name="see-also"></a>Consulte também  
 [Como instalar pré-requisitos com um aplicativo ClickOnce](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [Componente PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)
