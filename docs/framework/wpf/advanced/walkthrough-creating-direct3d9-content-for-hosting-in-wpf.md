---
title: 'Instruções passo a passo: criando conteúdo Direct3D9 para hospedar no WPF'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
ms.openlocfilehash: 321c4ba8659bd2226fff96e74e81ef24f0077c3d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580950"
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a>Instruções passo a passo: criando conteúdo Direct3D9 para hospedar no WPF
Esta instrução passo a passo mostra como criar conteúdo Direct3D9 adequado para hospedagem em um aplicativo do Windows Presentation Foundation (WPF). Para obter mais informações sobre hospedagem de conteúdo Direct3D9 em aplicativos WPF, consulte [Interoperação Direct3D9 e WPF](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).

 Nesta instrução passo a passo, as seguintes tarefas serão executadas:

-   Criar um projeto Direct3D9.

-   Configurar o projeto Direct3D9 para hospedagem em um aplicativo WPF.

 Ao terminar, você terá uma DLL com conteúdo Direct3D9 para uso em um aplicativo WPF.

## <a name="prerequisites"></a>Pré-requisitos
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:

-   Visual Studio 2010.

-   SDK do DirectX 9 ou versões posteriores.

## <a name="creating-the-direct3d9-project"></a>Criar o projeto Direct3D9
 A primeira etapa é criar e configurar um projeto Direct3D9.

#### <a name="to-create-the-direct3d9-project"></a>Criar o projeto Direct3D9

1.  Crie um novo Projeto Win32 no C++ chamado `D3DContent`.

     O Assistente de Aplicativo Win32 abrirá e exibirá a tela de boas-vindas.

2.  Clique em **Avançar**.

     A tela de Configurações do Aplicativo será exibida.

3.  Na seção **tipo de Aplicativo:**, selecione a opção **DLL**.

4.  Clique em **Finalizar**.

     O projeto D3DContent será gerado.

5.  No Gerenciador de Soluções, clique com o botão direito do mouse no projeto D3DContent e selecione **Propriedades**.

     A caixa de diálogo **Páginas de Propriedades do D3DContent** se abrirá.

6.  Selecione o nó **C/C++**.

7.  No campo **Diretórios de Inclusão Adicionais**, especifique o local da pasta de inclusão DirectX. O local padrão dessa pasta é %ProgramFiles%\Microsoft DirectX SDK (*version*)\Include.

8.  Clique duas vezes no nó **Vinculador** para expandi-lo.

9. No campo **Diretórios de Inclusão Adicionais**, especifique o local da pasta de bibliotecas do DirectX. O local padrão dessa pasta é %ProgramFiles%\Microsoft DirectX SDK (*version*)\Lib\x86.

10. Selecione o nó **Entrada**.

11. No campo **Dependências Adicionais**, adicione os arquivos `d3d9.lib` e `d3dx9.lib`.

12. No Gerenciador de Soluções, adicione um novo arquivo de definição de módulo (.def) chamado `D3DContent.def` ao projeto.

## <a name="creating-the-direct3d9-content"></a>Criar o conteúdo Direct3D9
 Para obter o melhor desempenho, o conteúdo Direct3D9 deve usar configurações específicas. O código a seguir mostra como criar uma superfície Direct3D9 com as melhores características de desempenho. Para obter mais informações, consulte [Considerações sobre Desempenho para Interoperabilidade entre Direct3D9 e WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).

#### <a name="to-create-the-direct3d9-content"></a>Para criar o conteúdo Direct3D9

1.  Usando o Gerenciador de Soluções, adicione três classes do C++ ao projeto nomeado como a seguir.

     `CRenderer` (com o destruidor virtual)

     `CRendererManager`

     `CTriangleRenderer`

2.  Abra o Renderer.h no Editor de Códigos e substitua o código gerado automaticamente pelo código a seguir.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]

3.  Abra o Renderer.cpp no Editor de Códigos e substitua o código gerado automaticamente pelo código a seguir.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]

4.  Abra o RendererManager.h no Editor de Códigos e substitua o código gerado automaticamente pelo código a seguir.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]

5.  Abra o RendererManager.cpp no Editor de Códigos e substitua o código gerado automaticamente pelo código a seguir.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]

6.  Abra o TriangleRenderer.h no Editor de Códigos e substitua o código gerado automaticamente pelo código a seguir.

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]

7.  Abra o TriangleRenderer.cpp no Editor de Códigos e substitua o código gerado automaticamente pelo código a seguir.

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]

8.  Abra o stdafx.h no Editor de Códigos e substitua o código gerado automaticamente pelo código a seguir.

     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]

9. Abra o dllmain.cpp no Editor de Códigos e substitua o código gerado automaticamente pelo código a seguir.

     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]

10. Abra o D3DContent.def no Editor de Códigos.

11. Substitua o código gerado automaticamente pelo código a seguir.

    ```
    LIBRARY "D3DContent"

    EXPORTS

    SetSize
    SetAlpha
    SetNumDesiredSamples
    SetAdapter

    GetBackBufferNoRef
    Render
    Destroy
    ```

12. Compile o projeto.

## <a name="next-steps"></a>Próximas etapas

-   Hospede o conteúdo Direct3D9 em um aplicativo WPF. Para obter mais informações, consulte [Instruções Passo a Passo: Hospedando Conteúdo Direct3D9 no WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Interop.D3DImage>
- [Considerações sobre Desempenho para Interoperabilidade entre Direct3D9 e WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [Instruções Passo a Passo: Hospedando Conteúdo Direct3D9 no WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)