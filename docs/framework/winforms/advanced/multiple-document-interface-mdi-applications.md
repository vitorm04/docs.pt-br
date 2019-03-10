---
title: Aplicativos de Interface de Documentos Múltiplos (MDI)
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 0ce7c66946d03d566b21473711cb6b3315885236
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717434"
---
# <a name="multiple-document-interface-mdi-applications"></a>Aplicativos de Interface de Documentos Múltiplos (MDI)
Aplicativos de interface de documentos múltiplos (MDI) permitem que você exiba vários documentos ao mesmo tempo, com cada documento exibido em sua própria janela. Aplicativos MDI geralmente têm um item de menu de Janela com submenus para alternar entre janelas ou documentos.  
  
> [!NOTE]
>  Existem algumas diferenças de comportamento entre formulários MDI e janelas da interface de documento único (SDI) nos Windows Forms. A propriedade `Opacity` não afeta a aparência dos formulários filho MDI. Além disso, o <xref:System.Windows.Forms.Form.CenterToParent%2A> método não afeta o comportamento dos formulários filho MDI.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Criar formulários pai MDI](how-to-create-mdi-parent-forms.md)  
 Fornece instruções para criar o contêiner para diversos documentos em um aplicativo MDI.  
  
 [Como: Criar formulários filho MDI](how-to-create-mdi-child-forms.md)  
 Fornece instruções de como criar uma ou mais janelas que operam em um formulário pai MDI.  
  
 [Como: Determinar o filho MDI ativo](how-to-determine-the-active-mdi-child.md)  
 Fornece instruções de como verificar a janela filho que tem o foco (e enviar seu conteúdo para a área de transferência).  
  
 [Como: Enviar dados para o filho MDI ativo](how-to-send-data-to-the-active-mdi-child.md)  
 Fornece instruções de como transportar informações para a janela filho ativa.  
  
 [Como: Organizar formulários filho MDI](how-to-arrange-mdi-child-forms.md)  
 Fornece instruções de como organizar lado a lado, em cascata ou organizar as janelas filho de um aplicativo MDI.
