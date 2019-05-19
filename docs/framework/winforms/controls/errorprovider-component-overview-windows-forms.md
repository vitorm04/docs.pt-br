---
title: Visão geral do componente ErrorProvider (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
ms.openlocfilehash: f2a97ab80cde00a47bbdf6830bdba325e1c9f3ef
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880967"
---
# <a name="errorprovider-component-overview-windows-forms"></a>Visão geral do componente ErrorProvider (Windows Forms)
O componente [ErrorProvider](errorprovider-component-windows-forms.md) dos Windows Forms é usado para validar a entrada do usuário em um formulário ou controle. Ele é normalmente usado junto com a validação de entrada do usuário em um formulário ou para exibir erros dentro de um conjunto de dados. Um provedor de erro é uma alternativa melhor que exibir uma mensagem de erro em uma caixa de mensagem, pois depois que uma caixa de mensagem for descartada, a mensagem de erro não estará mais visível. O <xref:System.Windows.Forms.ErrorProvider> componente exibe um ícone de erro (![um ponto de exclamação branco dentro de um círculo vermelho.](./media/errorprovider-component-overview-windows-forms/vb-error-provider-icon.gif)) ao lado de controle relevante, como uma caixa de texto; quando o usuário posiciona o ponteiro do mouse sobre o ícone de erro, uma dica de ferramenta é exibida, mostrando a cadeia de caracteres de mensagem de erro.  
  
## <a name="key-properties"></a>Propriedades da chave  
 O <xref:System.Windows.Forms.ErrorProvider> principais propriedades do componente estão <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>, e <xref:System.Windows.Forms.ErrorProvider.Icon%2A>. Ao usar <xref:System.Windows.Forms.ErrorProvider> componente com controles ligados a dados, o <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> propriedade deve ser definida para o recipiente apropriado (geralmente o formulário do Windows) para que o componente para exibir um ícone de erro no formulário. Quando o componente é adicionado no designer, o <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> estiver definida como o formulário que o contém; se você adicionar o controle no código, você deve configurá-lo por conta própria.  
  
 O <xref:System.Windows.Forms.ErrorProvider.Icon%2A> propriedade pode ser definida como um ícone de erro personalizada em vez do padrão. Quando o <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> propriedade for definida, o <xref:System.Windows.Forms.ErrorProvider> componente pode exibir mensagens de erro para um conjunto de dados. O método de chave de <xref:System.Windows.Forms.ErrorProvider> componente é o <xref:System.Windows.Forms.ErrorProvider.SetError%2A> método, que especifica a cadeia de caracteres de mensagem de erro e onde o ícone de erro deve aparecer.  
  
> [!NOTE]
>  O <xref:System.Windows.Forms.ErrorProvider> componente não fornece suporte interno para clientes de acessibilidade. Para tornar seu aplicativo acessível ao usar esse componente, você deve fornecer um mecanismo de comentários acessível adicional.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ErrorProvider>
- [Como: Exibir erros dentro de um conjunto de dados com o componente do Windows Forms ErrorProvider](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
- [Como: Exibir ícones de erro para validação do formulário com o componente do Windows Forms ErrorProvider](display-error-icons-for-form-validation-with-wf-errorprovider.md)
