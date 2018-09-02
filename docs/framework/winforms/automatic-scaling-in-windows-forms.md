---
title: Dimensionamento automático no Windows Forms
ms.date: 06/15/2017
helpviewer_keywords:
- scalability [Windows Forms], automatic in Windows Forms
- Windows Forms, automatic scaling
ms.assetid: 68fad25b-afbc-44bd-8e1b-966fc43507a4
ms.openlocfilehash: d3981be7977b56af0b60f9796519b78dc9ac5db3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43456646"
---
# <a name="automatic-scaling-in-windows-forms"></a>Dimensionamento automático no Windows Forms

Dimensionamento automático permite que um formulário e seus controles, criados em uma máquina com uma determinada exibição resolução ou sistema fonte, a ser exibida corretamente em outro computador com uma fonte de sistema ou resolução de exibição diferente. Ele garante que o formulário e seus controles de forma inteligente serão redimensionado para ser consistente com nativos do windows e outros aplicativos em computadores de usuários e outros desenvolvedores. O suporte a [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] para o dimensionamento automático e estilos visuais permite que [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] aplicativos para manter uma aparência consistente em comparação com aplicativos nativos do Windows na máquina de cada usuário.

Na maior parte, o dimensionamento automático funciona conforme o esperado em [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] versão 2.0 e posterior. No entanto, alterações de esquema de fonte podem ser problemáticas. Para obter um exemplo de como resolver esse problema, consulte [como: responder a alterações de esquema de fontes em um aplicativo do Windows Forms](how-to-respond-to-font-scheme-changes-in-a-windows-forms-application.md).

## <a name="need-for-automatic-scaling"></a>Necessidade de dimensionamento automático

Sem o dimensionamento automático, um aplicativo desenvolvido para resolução de tela ou fonte ou aparecerão muito pequeno ou muito grande quando que resolução ou a fonte é alterada. Por exemplo, se o aplicativo foi desenvolvido usando Tahoma 9 pontos como uma linha de base, sem ajuste ele aparecerá muito pequeno se executado em um computador em que a fonte do sistema é Tahoma 12 pontos. Elementos de texto, como títulos, menus, conteúdo da caixa de texto e assim por diante serão renderizado menores do que outros aplicativos. Além disso, o tamanho dos elementos de (UI) de interface do usuário que contêm texto, como muitos controles, menus e barra de título são dependentes da fonte usada. Neste exemplo, esses elementos também aparecerão relativamente menores.

Uma situação semelhante ocorre quando um aplicativo foi projetado para uma determinada resolução de vídeo. A resolução de vídeo mais comum é 96 pontos por polegada (DPI), que é igual a 100% dimensionamento da exibição, mas exibe de resolução mais alta que dão suporte a 125%, 150%, 200% (que 120 igual, respectivamente, 144 e 192 DPI) e superiores estão se tornando mais comum. Sem ajuste, um aplicativo, especialmente com base em elementos gráficos um, projetado para uma resolução aparecerá muito grande ou muito pequeno quando executado em outra resolução.

O dimensionamento automático procura contornar estes problemas redimensionando automaticamente o formulário e seus controles filho acordo com o tamanho da fonte relativa ou resolução de vídeo. O sistema operacional Windows dá suporte a dimensionamento automático das caixas de diálogo usando uma unidade de medida chamada unidades de diálogo relativa. Uma unidade de caixa de diálogo é baseada na fonte do sistema e sua relação com pixels pode ser determinada, no entanto, a função do SDK do Win32 `GetDialogBaseUnits`. Quando um usuário altera o tema usado pelo Windows, todas as caixas de diálogo são ajustadas automaticamente adequadamente. Além disso, o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] oferece suporte ao dimensionamento automático de acordo com a fonte padrão do sistema ou a resolução de vídeo. Opcionalmente, o dimensionamento automático pode ser desabilitado em um aplicativo.

## <a name="original-support-for-automatic-scaling"></a>Suporte original para dimensionamento automático

As versões 1.0 e 1.1 do [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] suporte para dimensionamento automático de uma maneira simples que era dependente da fonte padrão do Windows usada para a interface do usuário, representada pelo valor do SDK do Win32 **DEFAULT_GUI_FONT**. Essa fonte normalmente é alterada somente quando a resolução de vídeo é alterado. O mecanismo a seguir foi usado para implementar o dimensionamento automático:

1. Em tempo de design, o <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> propriedade (que agora foi preterida) foi definida como a altura e largura da fonte padrão do sistema no computador de desenvolvedor.

2. Em tempo de execução, a fonte padrão do sistema de computador do usuário foi usado para inicializar o <xref:System.Windows.Forms.Control.Font%2A> propriedade do <xref:System.Windows.Forms.Form> classe.

3. Antes de exibir o formulário, o <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> método foi chamado para dimensionar o formulário. Esse método calculados os tamanhos de escala relativa de <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> e <xref:System.Windows.Forms.Control.Font%2A> , em seguida, chamado de <xref:System.Windows.Forms.Control.Scale%2A> método, na verdade, dimensionar o formulário e seus filhos.

4. O valor de <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> era atualizado de modo que os próximos chamadas para <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> progressivamente não redimensione o formulário.

Embora esse mecanismo era suficiente para a maioria das finalidades, ele sofria das seguintes limitações:

- Uma vez que o <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> propriedade representa o tamanho da fonte base como valores inteiros, se ocorrerem erros de arredondamento que tornam-se evidente quando um formulário é alternado através de várias resoluções.

- O dimensionamento automático implementado na apenas o <xref:System.Windows.Forms.Form> classe, não no <xref:System.Windows.Forms.ContainerControl> classe. Como resultado, os controles de usuário dimensionará corretamente somente quando o controle de usuário foi criado com a mesma resolução como o formulário, e ele foi colocado no formulário em tempo de design.

- Formulários e seus controles filho podem apenas ser criados simultaneamente por vários desenvolvedores se suas soluções de máquina eram os mesmos. Da mesma forma ela também torna a herança de um formulário depende da resolução associada ao formulário pai.

- Não é compatível com os gerentes de layout mais recentes introduzidos com o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] versão 2.0, tais como <xref:System.Windows.Forms.FlowLayoutPanel> e <xref:System.Windows.Forms.TableLayoutPanel>.

- Ele não oferecia suporte ao dimensionamento baseado diretamente na resolução de vídeo que é necessária para compatibilidade com o [!INCLUDE[compact](../../../includes/compact-md.md)].

Embora esse mecanismo é preservado no [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] versão 2.0 para manter a compatibilidade com versões anteriores, ela foi substituída pelo mecanismo de dimensionamento mais robusto descrito a seguir. Como consequência, o <xref:System.Windows.Forms.Form.AutoScale%2A>, <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A>, <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A>e certos <xref:System.Windows.Forms.Control.Scale%2A> sobrecargas são marcadas como obsoletas.

> [!NOTE]
> Você pode excluir com segurança as referências a esses membros quando você atualiza seu código herdado para o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] versão 2.0.

## <a name="current-support-for-automatic-scaling"></a>Suporte atual para o dimensionamento automático

O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] versão 2.0 supera as limitações anteriores, introduzindo as seguintes alterações para o dimensionamento automático de formulários do Windows:

- Suporte básico para dimensionamento foi movido para o <xref:System.Windows.Forms.ContainerControl> de classe para que os formulários, controles compostos nativos e controles de usuário recebam suporte de colocação em escala uniforme. Os novos membros <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> e <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> foram adicionados.

- O <xref:System.Windows.Forms.Control> classe também possui diversos novos membros que permitem que ele participe de dimensionamento e dar suporte ao dimensionamento misto no mesmo formulário. Especificamente o <xref:System.Windows.Forms.Control.Scale%2A>, <xref:System.Windows.Forms.Control.ScaleChildren%2A>, e <xref:System.Windows.Forms.Control.GetScaledBounds%2A> membros dão suporte ao dimensionamento.

- Suporte para dimensionamento com base na resolução de tela foi adicionado para complementar o suporte de fonte do sistema, conforme definido pelo <xref:System.Windows.Forms.AutoScaleMode> enumeração. Esse modo é compatível com o dimensionamento automático com suporte a [!INCLUDE[compact](../../../includes/compact-md.md)] habilitando a migração fácil de aplicativos.

- Compatibilidade com os gerentes de layout, como <xref:System.Windows.Forms.FlowLayoutPanel> e <xref:System.Windows.Forms.TableLayoutPanel> foi adicionado para a implementação de dimensionamento automático.

- Fatores de dimensionamento agora é representado como valores de ponto, normalmente usando flutuante o <xref:System.Drawing.SizeF> estruturar, de forma que os erros de arredondamento foram praticamente eliminados.

> [!CAUTION]
> Não há suporte para misturas arbitrárias de DPI e modos de dimensionamento de fonte. Embora você pode dimensionar um controle de usuário usando um modo (por exemplo, DPI) e colocá-lo em um formulário usando outro modo (fonte) sem problemas, mas a combinação de um formulário de base em um modo e um formulário derivado em outro pode levar a resultados inesperados.

### <a name="automatic-scaling-in-action"></a>Dimensionamento automático em ação

Agora, o Windows Forms usa a seguinte lógica para dimensionar automaticamente os formulários e seu conteúdo:

1. Em tempo de design, cada <xref:System.Windows.Forms.ContainerControl> registra o modo de dimensionamento e sua resolução atual em de <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> e <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>, respectivamente.

2. Em tempo de execução, a resolução real é armazenada no <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> propriedade. O <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A> propriedade dinamicamente calcula a proporção entre a resolução de colocação em escala de tempo de execução e tempo de design.

3. Quando o formulário carrega, se os valores de <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> e <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> forem diferentes, então o <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> método é chamado para dimensionar o controle e seus filhos. Este método suspende o layout e chama o <xref:System.Windows.Forms.Control.Scale%2A> método para executar o dimensionamento real. Depois disso, o valor de <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> é atualizado para evitar dimensionamento progressivo.

4. <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> é também chamado automaticamente nas seguintes situações:

    - Em resposta à <xref:System.Windows.Forms.Control.OnFontChanged%2A> evento se o modo de dimensionamento é <xref:System.Windows.Forms.AutoScaleMode.Font>.

    - Quando o layout do controle recipiente é retomado e uma alteração for detectado na <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> ou <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> propriedades.

    - Como indicado acima, quando um pai <xref:System.Windows.Forms.ContainerControl> está sendo dimensionado. Cada controle de contêiner é responsável por dimensionar seus filhos usando seus próprios fatores de dimensionamento e não aquele do seu contêiner pai.

5. Controles filho podem modificar seu comportamento de dimensionamento por vários meios:

    - O <xref:System.Windows.Forms.Control.ScaleChildren%2A> propriedade pode ser substituída para determinar se os seus controles filho devem ser escalados ou não.

    - O <xref:System.Windows.Forms.Control.GetScaledBounds%2A> método pode ser substituído para ajustar os limites que o controle é dimensionado, mas não a lógica de dimensionamento.

    - O <xref:System.Windows.Forms.Control.ScaleControl%2A> método pode ser substituído para alterar a lógica de dimensionamento para o controle atual.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>
- <xref:System.Windows.Forms.Control.Scale%2A>
- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>
- [Renderizando controles com estilos visuais](./controls/rendering-controls-with-visual-styles.md)
- [Como Melhorar o Desempenho Evitando a Colocação em Escala Automática](./advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)