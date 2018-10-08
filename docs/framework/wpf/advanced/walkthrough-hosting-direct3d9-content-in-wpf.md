---
title: 'Instruções passo a passo: hospedando conteúdo de Direct3D9 no WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: 1fa4c2347448e23bbf740093541ec2b834df6705
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48849862"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a>Instruções passo a passo: hospedando conteúdo de Direct3D9 no WPF
Esta instrução passo a passo mostra como hospedar o conteúdo Direct3D9 em um aplicativo do Windows Presentation Foundation (WPF).  
  
 Nesta instrução passo a passo, as seguintes tarefas serão executadas:  
  
-   Crie um projeto WPF para hospedar o conteúdo Direct3D9.  
  
-   Importe o conteúdo Direct3D9.  
  
-   Exibir o conteúdo de Direct3D9 usando a <xref:System.Windows.Interop.D3DImage> classe.  
  
 Quando tiver terminado, você saberá como hospedar conteúdo Direct3D9 em um aplicativo WPF.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   Visual Studio.  
  
-   DirectX SDK 9 ou posterior.  
  
-   Uma DLL que contém o conteúdo Direct3D9 em um formato compatível com WPF. Para obter mais informações, consulte [Interoperação de WPF e Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) e [Instrução passo a passo: criando conteúdo Direct3D9 para hospedar em WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
## <a name="creating-the-wpf-project"></a>Criando o projeto WPF  
 A primeira etapa é criar o projeto do aplicativo do WPF.  
  
#### <a name="to-create-the-wpf-project"></a>Para criar o projeto WPF  
  
-   Crie um novo projeto de aplicativo do WPF no Visual C#, chamado `D3DHost`. Para obter mais informações, consulte [Como criar um novo projeto de aplicativo do WPF](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
     MainWindow.xaml é aberto no [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
## <a name="importing-the-direct3d9-content"></a>Importando o conteúdo Direct3D9  
 Importar o conteúdo de Direct3D9 de uma DLL não gerenciada usando o `DllImport` atributo.  
  
#### <a name="to-import-direct3d9-content"></a>Para importar o conteúdo Direct3D9  
  
1.  Abra MainWindow.xaml.cs no Editor de códigos.  
  
2.  Substitua o código gerado automaticamente pelo código a seguir.  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a>Hospedando o conteúdo Direct3D9  
 Por fim, use o <xref:System.Windows.Interop.D3DImage> classe para hospedar o conteúdo de Direct3D9.  
  
#### <a name="to-host-the-direct3d9-content"></a>Para hospedar o conteúdo Direct3D9  
  
1.  Em MainWindow.xaml, substitua o XAML gerado automaticamente pelo seguinte XAML.  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  Compile o projeto.  
  
3.  Copie a DLL que contém o conteúdo Direct3D9 para a pasta lixeira/Debug.  
  
4.  Pressione F5 para executar o projeto.  
  
     O conteúdo Direct3D9 aparece dentro do aplicativo do WPF.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Interop.D3DImage>  
 [Considerações sobre Desempenho para Interoperabilidade entre Direct3D9 e WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
