---
title: Implantando aplicativos que referenciam o componente PrintForm (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
ms.openlocfilehash: 78d332c88b45fa9b1204d9d5352a6027409254e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562421"
---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a>Implantando aplicativos que referenciam o componente PrintForm (Visual Basic)
Se você quiser implantar um aplicativo que faz referência a <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente, o componente deve ser instalado no computador de destino.  
  
 Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá-los na [Centro de Download](https://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## <a name="installing-the-printform-as-a-prerequisite"></a>Instalando o PrintForm como um pré-requisito  
 Para implantar um aplicativo com êxito, você também deve implantar todos os componentes que são referenciados pelo aplicativo. O processo de instalação de componentes de pré-requisito é conhecido como *inicialização*.  
  
 Quando o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente estiver instalado no computador de desenvolvimento, um pacote de bootstrapper do Microsoft Visual Basic Power Packs é adicionado ao diretório de bootstrapper do Visual Studio. Este pacote está disponível, em seguida, quando você seguir os procedimentos de adição de pré-requisitos para qualquer um [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] ou implantação do Windows Installer.  
  
 Por padrão, os componentes inicializados são implantados no mesmo local do pacote de instalação. Como alternativa, você pode optar por implantar os componentes de um local de compartilhamento de arquivo ou URL da qual os usuários podem baixá-los conforme necessário.  
  
> [!NOTE]
>  Para instalar os componentes inicializados, o usuário talvez precise de permissões de usuário administrativo ou semelhante no computador. Para [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplicativos, isso significa que o usuário precisará de permissões administrativas para instalar o aplicativo, independentemente do nível de segurança especificado pelo aplicativo. Depois que o aplicativo é instalado, o usuário pode executar o aplicativo sem permissões administrativas.  
  
 Durante a instalação, os usuários serão solicitados a instalar o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente se não estiver presente no computador de destino.  
  
 Como alternativa para a inicialização, você pode implantar previamente o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> componente usando um sistema de distribuição eletrônica de software, como o Microsoft Systems Management Server.  
  
## <a name="see-also"></a>Consulte também
- [Como: Instalar pré-requisitos com um aplicativo ClickOnce](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)
- [Componente PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)
