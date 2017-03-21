---
title: Implantando aplicativos que referenciam o componente PrintForm (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 016643329d2ee66ca5a32f155cf91e0ee137f38f
ms.lasthandoff: 03/13/2017

---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a>Implantando aplicativos que referenciam o componente PrintForm (Visual Basic)
Se desejar implantar um aplicativo que faz referência a <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente, o componente deve ser instalado no computador de destino.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
 Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá-los no [Centro de Download](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## <a name="installing-the-printform-as-a-prerequisite"></a>Instalando o PrintForm como um pré-requisito  
 Para implantar um aplicativo com êxito, você também deve implantar todos os componentes que são referenciados pelo aplicativo. O processo de instalação de componentes de pré-requisito é conhecido como *inicialização*.  
  
 Quando o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente é instalado em seu computador de desenvolvimento, um pacote de bootstrapper do Microsoft Visual Basic Power Packs é adicionado para o [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] directory bootstrapper.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Este pacote estará disponível quando você seguir os procedimentos de adição de pré-requisitos para o [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] ou implantação do Windows Installer.  
  
 Por padrão, os componentes inicializados são implantados no mesmo local que o pacote de instalação. Como alternativa, você pode optar por implantar os componentes de um local de compartilhamento de arquivo ou URL da qual os usuários podem baixá-los conforme necessário.  
  
> [!NOTE]
>  Para instalar componentes inicializados, o usuário talvez precise de permissões de usuário administrativo ou semelhante no computador. Para [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] aplicativos, isso significa que o usuário deverá ter permissões administrativas para instalar o aplicativo, independentemente do nível de segurança especificado pelo aplicativo. Depois que o aplicativo é instalado, o usuário pode executar o aplicativo sem permissões administrativas.  
  
 Durante a instalação, os usuários serão solicitados a instalar o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente se ele não está presente no computador de destino.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
 Como alternativa para a inicialização, você pode implantar previamente o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente usando um sistema de distribuição eletrônica de software como o Microsoft Systems Management Server.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
## <a name="see-also"></a>Consulte também  
 [Como instalar pré-requisitos com um aplicativo ClickOnce](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5)   
 [Componente PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)
