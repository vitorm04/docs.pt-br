---
title: "Caixa de di&#225;logo Refatora&#231;&#227;o e Renomear (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.RenameSymbol"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "nomes, alterando símbolo"
  - "Caixa de diálogo Renomear"
  - "símbolos, renomeando"
ms.assetid: 001d2d81-9bb6-4e8e-ae3a-20c0daaa3959
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Caixa de di&#225;logo Refatora&#231;&#227;o e Renomear (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Use a caixa de diálogo **Rename** do Visual Basic para renomear identificadores em seu código para símbolos como campos, variáveis locais, métodos, namespaces, propriedades e tipos.  Você pode abrir a caixa de diálogo **Rename** clicando com o botão direito do mouse na declaração de elemento.  
  
 **Novo nome**  
 Especifica o novo nome para o elemento de código.  
  
 **Local**  
 Identifica o namespace para pesquisar quando você executar a operação de renomeação.  
  
## Operações de renomeação  
 A caixa de diálogo **Rename** executa operações de renomeação ligeiramente diferentes, dependendo do tipo de elemento renomeado.  
  
|Tipo de elemento|Operação de renomeação|  
|----------------------|----------------------------|  
|Classe|Altera todas as declarações e todos os usos da classe para o novo nome.  Para classes parcial, a operação de renomeação se propaga para todas as partes.|  
|Campo|Altera a declaração e usos do campo para o novo nome.|  
|Variável local|Altera a declaração e usos da variável para o novo nome.|  
|Método|Altera o nome do método e todas as referências a esse método para o novo nome.|  
|Namespace|Altera o nome do namespace para o novo nome, na declaração, em todas as instruções `Imports` e todos os nomes totalmente qualificados.|  
|Propriedade|Altera a declaração e usos da propriedade para o novo nome.|  
  
## Refatoração  
 Para proporcionar uma experiência completa de refatoração, o Visual Basic fez uma parceria com a Developer Express Inc.  Para obter suporte à refatoração.  Consulte [Refactor\!](http://go.microsoft.com/fwlink/?LinkId=155788) do Visual Basic de MSDN Developer Center para obter mais detalhes e instruções sobre como baixar essa ferramenta.  O Refactor\!  oferece suporte a mais de 15 recursos individuais de refatoração.  Isso inclui operações tais como Reodenar Parâmetros,  Método de Extração, Encapsular Campos e Criar Overload.  
  
## Consulte também  
 [Usando o ambiente de desenvolvimento do Visual Basic](../../../visual-basic/developing-apps/using-ide/using-the-visual-basic-development-environment.md)