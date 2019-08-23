---
title: Aplicativos de Interface de Documentos Múltiplos (MDI)
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 23e0275d5e6b081ec02d669a78e8695453360637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956555"
---
# <a name="multiple-document-interface-mdi-applications"></a>Aplicativos de Interface de Documentos Múltiplos (MDI)
Aplicativos de interface de documentos múltiplos (MDI) permitem que você exiba vários documentos ao mesmo tempo, com cada documento exibido em sua própria janela. Aplicativos MDI geralmente têm um item de menu de Janela com submenus para alternar entre janelas ou documentos.  
  
> [!NOTE]
> Existem algumas diferenças de comportamento entre formulários MDI e janelas da interface de documento único (SDI) nos Windows Forms. A propriedade `Opacity` não afeta a aparência dos formulários filho MDI. Além disso, <xref:System.Windows.Forms.Form.CenterToParent%2A> o método não afeta o comportamento de formulários filho MDI.  
  
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
