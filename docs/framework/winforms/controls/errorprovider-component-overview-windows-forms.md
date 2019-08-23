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
ms.openlocfilehash: 3cfd3f306d4a18ce8a194b5197060fbca1d157d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965296"
---
# <a name="errorprovider-component-overview-windows-forms"></a>Visão geral do componente ErrorProvider (Windows Forms)
O componente [ErrorProvider](errorprovider-component-windows-forms.md) dos Windows Forms é usado para validar a entrada do usuário em um formulário ou controle. Ele é normalmente usado junto com a validação de entrada do usuário em um formulário ou para exibir erros dentro de um conjunto de dados. Um provedor de erro é uma alternativa melhor que exibir uma mensagem de erro em uma caixa de mensagem, pois depois que uma caixa de mensagem for descartada, a mensagem de erro não estará mais visível. O <xref:System.Windows.Forms.ErrorProvider> componente exibe um ícone de erro![(um ponto de exclamação branco](./media/errorprovider-component-overview-windows-forms/vb-error-provider-icon.gif)dentro de um círculo vermelho) ao lado do controle relevante, como uma caixa de texto; quando o usuário posiciona o ponteiro do mouse sobre o ícone de erro, uma dica de ferramenta é exibida, mostrando a cadeia de caracteres de mensagem de erro.  
  
## <a name="key-properties"></a>Propriedades da chave  
 As <xref:System.Windows.Forms.ErrorProvider> Propriedades de chave do componente <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>são <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>, e <xref:System.Windows.Forms.ErrorProvider.Icon%2A>. Ao usar <xref:System.Windows.Forms.ErrorProvider> o componente com controles vinculados a dados <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> , a propriedade deve ser definida como o contêiner apropriado (geralmente o Windows Form) para que o componente exiba um ícone de erro no formulário. Quando o componente é adicionado ao designer, a <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> propriedade é definida como o formulário que a contém; se você adicionar o controle no código, deverá configurá-lo por conta própria.  
  
 A <xref:System.Windows.Forms.ErrorProvider.Icon%2A> propriedade pode ser definida como um ícone de erro personalizado em vez do padrão. Quando a <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> propriedade é definida, o <xref:System.Windows.Forms.ErrorProvider> componente pode exibir mensagens de erro para um conjunto de uma. O método de chave do <xref:System.Windows.Forms.ErrorProvider> componente é o <xref:System.Windows.Forms.ErrorProvider.SetError%2A> método, que especifica a cadeia de caracteres de mensagem de erro e onde o ícone de erro deve aparecer.  
  
> [!NOTE]
> O <xref:System.Windows.Forms.ErrorProvider> componente não fornece suporte interno para clientes de acessibilidade. Para tornar seu aplicativo acessível ao usar esse componente, você deve fornecer um mecanismo de comentários acessível adicional.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ErrorProvider>
- [Como: Exibir erros em um conjunto de um DataSet com o componente Windows Forms ErrorProvider](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
- [Como: Exibir ícones de erro para validação de formulário com o componente Windows Forms ErrorProvider](display-error-icons-for-form-validation-with-wf-errorprovider.md)
