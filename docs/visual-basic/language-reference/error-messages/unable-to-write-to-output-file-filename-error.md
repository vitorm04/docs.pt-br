---
title: "Não é possível gravar no arquivo de saída &quot;&lt;filename&gt;&quot;: &lt;erro&gt; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31019
- bc31019
dev_langs:
- VB
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fe093ec3b36ba733cb9b0c162e242c8dce6b7c78
ms.lasthandoff: 03/13/2017

---
# <a name="unable-to-write-to-output-file-39ltfilenamegt39-lterrorgt"></a>Não é possível gravar no arquivo de saída '&lt;filename&gt;': &lt;erro&gt;
Ocorreu um problema na criação do arquivo.  
  
 Não foi possível abrir um arquivo de saída para gravação. O arquivo (ou a pasta que contém o arquivo) pode estar aberto para uso exclusivo por outro processo ou pode ter seu atributo definido como somente leitura.  
  
 Algumas situações comuns em que um arquivo fica aberto exclusivamente são quando:  
  
-   O aplicativo está em execução e usando os arquivos dele. Para resolver esse problema, verifique se o aplicativo não está em execução.  
  
-   Outro aplicativo abriu o arquivo. Para resolver esse problema, verifique se nenhum outro aplicativo está acessando os arquivos. Nem sempre é óbvio qual aplicativo está acessando seus arquivos. Nesse caso, reiniciar o computador pode ser o caminho mais fácil para encerrar o aplicativo.  
  
 Se apenas um dos arquivos de saída do projeto estiver marcado como somente leitura, esta exceção será acionada.  
  
 **ID do erro:** BC31019  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Compile o programa novamente para verificar se o erro persiste.  
  
2.  Se o erro persistir, salve seu trabalho e reinicie o [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)].  
  
3.  Se o erro persistir, reinicie o computador.  
  
4.  Se o erro persistir, reinstale o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
5.  Se o erro persistir após a reinstalação, notifique o Microsoft Product Support Services.  
  
### <a name="to-check-file-attributes-in-file-explorer"></a>Para verificar atributos de arquivo no Explorador de Arquivos  
  
1.  Abra a pasta que lhe interessa.  
  
2.  Clique o **exibições** ícone e escolha **detalhes**.  
  
3.  Clique com botão direito no cabeçalho da coluna e escolha **atributos** na lista suspensa.  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a>Para alterar os atributos de um arquivo ou pasta  
  
1.  Em **File Explorer**, com o botão direito no arquivo ou pasta e escolha **propriedades**.  
  
2.  No **atributos** seção o **geral** guia, desmarque o **somente leitura** caixa.  
  
3.  Press **OK**.  
  
## <a name="see-also"></a>Consulte também  
 [Fale conosco](https://docs.microsoft.com/visualstudio/ide/talk-to-us)
