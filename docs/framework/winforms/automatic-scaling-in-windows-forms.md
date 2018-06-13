---
title: Dimensionamento automático no Windows Forms
ms.date: 06/15/2017
helpviewer_keywords:
- scalability [Windows Forms], automatic in Windows Forms
- Windows Forms, automatic scaling
ms.assetid: 68fad25b-afbc-44bd-8e1b-966fc43507a4
ms.openlocfilehash: e27c56d9a6d745c7d1ff83986e7996aa1bebc879
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529877"
---
# <a name="automatic-scaling-in-windows-forms"></a>Dimensionamento automático em Windows Forms
Dimensionamento automático permite que um formulário e seus controles criados em uma máquina com uma determinada exibição resolução ou sistema de fonte, a ser exibido corretamente em outro computador com uma fonte de sistema ou resolução de exibição diferente. Ela garante que o formulário e seus controles serão inteligentemente redimensionados para ser consistente com nativos do windows e outros aplicativos em computadores dos usuários e outros desenvolvedores. O suporte a [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] para dimensionamento automático e estilos visuais permite [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] aplicativos para manter uma aparência consistente quando comparado a aplicativos nativos do Windows na máquina de cada usuário.
  
A maior parte do tempo, o dimensionamento automático funciona conforme o esperado em [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] versão 2.0 e posteriores. No entanto, alterações de esquema de fonte podem ser problemáticas. Para ver um exemplo de como resolver esse problema, consulte [como: responder a alterações no esquema de fontes em um aplicativo do Windows Forms](how-to-respond-to-font-scheme-changes-in-a-windows-forms-application.md).
  
## <a name="need-for-automatic-scaling"></a>Necessidade de dimensionamento automático  
Sem o dimensionamento automático, um aplicativo desenvolvido para resolução de tela ou fonte ou aparecerão muito grande ou muito pequeno quando que resolução ou a fonte é alterada. Por exemplo, se o aplicativo é criado usando Tahoma 9 pontos como uma linha de base, sem ajuste ele aparecerá muito pequeno se executado em um computador em que a fonte do sistema é Tahoma 12 pontos. Elementos de texto, como títulos, menus, conteúdo da caixa de texto e assim por diante serão renderizado menores do que outros aplicativos. Além disso, o tamanho dos elementos de interface de usuário que contêm texto, como a barra de título, menus e muitos controles dependem da fonte usada. Neste exemplo, esses elementos também aparecerão relativamente menores.

Uma situação análoga ocorre quando um aplicativo foi projetado para uma determinada resolução de vídeo. A resolução de vídeo mais comum é 96 pontos por polegada (DPI), que é igual a 100% dimensionamento da exibição, mas exibe de resolução superior com suporte de 125%, 150%, 200% (quais 120 respectivamente igual, 144 e 192 DPI) e acima estão se tornando mais comuns. Sem ajuste, um aplicativo, especialmente baseados em gráficos um, projetado para uma resolução aparecerá muito grande ou muito pequeno quando executado em outra resolução.

O dimensionamento automático procura contornar estes problemas redimensionando automaticamente o formulário e seus controles filhos de acordo com o tamanho da fonte relativa ou resolução de vídeo. O sistema operacional Windows oferece suporte ao dimensionamento automático das caixas de diálogo usando uma unidade de medida chamada unidades de diálogo relativa. Uma unidade de diálogo é baseada na fonte do sistema e sua relação com pixels pode ser determinada através de função do SDK do Win32 `GetDialogBaseUnits`. Quando um usuário altera o tema usado pelo Windows, todas as caixas de diálogo são ajustadas automaticamente adequadamente. Além disso, o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] oferece suporte ao dimensionamento automático de acordo com a fonte padrão do sistema ou a resolução de vídeo. Opcionalmente, o dimensionamento automático pode ser desabilitado em um aplicativo.

## <a name="original-support-for-automatic-scaling"></a>Suporte original para dimensionamento automático
As versões 1.0 e 1.1 do [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] suporte ao dimensionamento automático de uma maneira simples que era dependente da fonte padrão do Windows usada para a interface do usuário, representado pelo valor do SDK do Win32 **DEFAULT_GUI_FONT**. Essa fonte normalmente só é alterada quando a resolução de vídeo é alterado. O mecanismo a seguir foi usado para implementar o dimensionamento automático:

1. Em tempo de design, o <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> (que agora está obsoleta) foi definida como a altura e largura da fonte padrão do sistema no computador do desenvolvedor.

2. Em tempo de execução, a fonte padrão do sistema do computador do usuário foi usado para inicializar o <xref:System.Windows.Forms.Control.Font%2A> propriedade o <xref:System.Windows.Forms.Form> classe.

3. Antes de exibir o formulário, o <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> método foi chamado para dimensionar o formulário. Esse método calculados os tamanhos de escala relativa de <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> e <xref:System.Windows.Forms.Control.Font%2A> chamado o <xref:System.Windows.Forms.Control.Scale%2A> método para dimensionar o formulário e seus filhos.

4. O valor de <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> foi atualizado de modo que subsequentes chamadas para <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> não redimensionassem o formulário.

Enquanto esse mecanismo estava suficiente para a maioria das finalidades, ele sofreu das seguintes limitações:

- Desde o <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> propriedade representa o tamanho da fonte base como valores inteiros, ocorriam erros de arredondamento que se tornam evidentes quando um formulário é alternado através de várias resoluções.

- O dimensionamento automático foi implementado somente o <xref:System.Windows.Forms.Form> classe, não de <xref:System.Windows.Forms.ContainerControl> classe. Como resultado, os controles de usuário seriam dimensionar corretamente somente quando o controle de usuário foi criado com a mesma resolução do formulário e ele foi colocado no formulário em tempo de design.

- Formulários e seus controles filhos podem somente ser criados simultaneamente por vários desenvolvedores se suas soluções de máquina eram os mesmos. Da mesma forma ela também torna a herança de um formulário depende da resolução associada ao formulário pai.

> [!NOTE]
> Com as diferenças extremas na exibição DPIs, especialmente em dispositivos modernos de 2-em-1, isso ainda poderá ocorrer com as versões mais recentes do .NET Framework e do Visual Studio. Para resolver isso em uma equipe usando diferentes exibições DPI, certifique-se de que o Visual Studio sempre inicia em um modo sem reconhecimento de DPI, para que o designer de formulários do Windows sempre baseia o cálculo do layout em 96 DPI. Para esse fim, basta defina a seguinte chave do registro para desabilitar o reconhecimento de HighDPI do Visual Studio:
>
> ```
> [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe]
> "dpiAwareness"=dword:00000000
> ```

- Não é compatível com os gerentes de layout mais recentes introduzidos com o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] versão 2.0, como <xref:System.Windows.Forms.FlowLayoutPanel> e <xref:System.Windows.Forms.TableLayoutPanel>.

- Ele não oferecia suporte ao dimensionamento baseado diretamente na resolução de vídeo que é necessária para compatibilidade com o [!INCLUDE[compact](../../../includes/compact-md.md)].

Embora esse mecanismo é mantido no [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] versão 2.0 para manter a compatibilidade com versões anteriores, ele foi substituído pelo mecanismo de dimensionamento mais robusto descrito a seguir. Como consequência, o <xref:System.Windows.Forms.Form.AutoScale%2A>, <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A>, <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A>e determinados <xref:System.Windows.Forms.Control.Scale%2A> sobrecargas são marcadas como obsoletas.

> [!NOTE]
> Você pode excluir com segurança as referências a esses membros quando você atualiza seu código herdado para o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] versão 2.0.

## <a name="current-support-for-automatic-scaling"></a>Suporte atual para dimensionamento automático
O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] versão 2.0 supera as limitações anteriores, introduzindo as seguintes alterações no dimensionamento automático de formulários do Windows:

- Suporte básico para dimensionamento foi movido para o <xref:System.Windows.Forms.ContainerControl> de classe para que formulários, controles compostos nativos e controles de usuário recebam suporte uniforme ao dimensionamento. Os novos membros <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> e <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> foram adicionados.

- O <xref:System.Windows.Forms.Control> classe também possui diversos novos membros que permitem que ele participe de dimensionamento e dar suporte ao dimensionamento misto no mesmo formulário. Especificamente o <xref:System.Windows.Forms.Control.Scale%2A>, <xref:System.Windows.Forms.Control.ScaleChildren%2A>, e <xref:System.Windows.Forms.Control.GetScaledBounds%2A> membros oferecem suporte ao dimensionamento.

- Suporte para dimensionamento com base na resolução da tela foi adicionado para complementar o suporte de fonte do sistema, conforme definido pelo <xref:System.Windows.Forms.AutoScaleMode> enumeração. Esse modo é compatível com o dimensionamento automático com suporte a [!INCLUDE[compact](../../../includes/compact-md.md)] permitindo mais fácil migração de aplicativos.

- Compatibilidade com os gerentes de layout, como <xref:System.Windows.Forms.FlowLayoutPanel> e <xref:System.Windows.Forms.TableLayoutPanel> foi adicionada à implementação de dimensionamento automático.

- Fatores de dimensionamento agora é representado como valores de ponto, normalmente usando flutuante o <xref:System.Drawing.SizeF> estrutura, para que os erros de arredondamento foram praticamente eliminados.

> [!CAUTION]
> Não há suporte para misturas arbitrárias de DPI e fonte modos de dimensionamento. Embora você pode dimensionar um controle de usuário usando um modo (por exemplo, DPI) e colocá-lo em um formulário usando outro modo (fonte) sem problemas, mas a combinação de um formulário base em um modo e um formulário derivado em outro pode levar a resultados inesperados.

### <a name="automatic-scaling-in-action"></a>Dimensionamento automático em ação
Agora, o Windows Forms usa a seguinte lógica para dimensionar automaticamente os formulários e seu conteúdo:

1. Em tempo de design, cada <xref:System.Windows.Forms.ContainerControl> registra o modo de dimensionamento e sua resolução atual do <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> e <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>, respectivamente.

2. Em tempo de execução, a resolução real é armazenada no <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> propriedade. O <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A> propriedade dinamicamente calcula a proporção entre a resolução de dimensionamento do tempo de execução e tempo de design.

3. Quando o formulário é carregado, se os valores de <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> e <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> forem diferentes, então o <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> método é chamado para dimensionar o controle e seus filhos. Este método suspende o layout e chama o <xref:System.Windows.Forms.Control.Scale%2A> método para executar o dimensionamento real. Posteriormente, o valor de <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> é atualizado para evitar dimensionamento progressivo.

4. <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> é também chamado automaticamente nas seguintes situações:

    - Em resposta ao <xref:System.Windows.Forms.Control.OnFontChanged%2A> evento se o modo de dimensionamento é <xref:System.Windows.Forms.AutoScaleMode.Font>.
  
    - Quando o layout do controle recipiente é retomado e uma alteração for detectado no <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> ou <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> propriedades.
  
    - Como indicado acima, quando um pai <xref:System.Windows.Forms.ContainerControl> está sendo dimensionado. Cada controle recipiente é responsável por dimensionar seus filhos usando seus próprios fatores de dimensionamento e não aquele do seu contêiner pai.

5. Controles filho podem modificar seu comportamento de dimensionamento por vários meios:

    - O <xref:System.Windows.Forms.Control.ScaleChildren%2A> propriedade pode ser substituída para determinar se seus controles filhos devem ser dimensionados ou não.

    - O <xref:System.Windows.Forms.Control.GetScaledBounds%2A> método pode ser substituído para ajustar os limites que o controle é dimensionado, mas não a lógica de dimensionamento.

    - O <xref:System.Windows.Forms.Control.ScaleControl%2A> método pode ser substituído para alterar a lógica de dimensionamento do controle atual.

## <a name="see-also"></a>Consulte também
 <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>  
 <xref:System.Windows.Forms.Control.Scale%2A>  
 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>  
 <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>  
 [Renderizando controles com estilos visuais](./controls/rendering-controls-with-visual-styles.md)  
 [Como Melhorar o Desempenho Evitando a Colocação em Escala Automática](./advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)
