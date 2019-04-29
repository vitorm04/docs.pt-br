---
title: "Não é possível gravar no arquivo de saída '<filename>': <error>"
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: f29eb628c079f65a520cf5e1ccd8afed549f7cad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787407"
---
# <a name="unable-to-write-to-output-file-filename-error"></a>Não é possível gravar no arquivo de saída '\<filename >': \<erro >
Ocorreu um problema na criação do arquivo.  
  
 Não foi possível abrir um arquivo de saída para gravação. O arquivo (ou a pasta que contém o arquivo) pode estar aberto para uso exclusivo por outro processo ou pode ter seu atributo definido como somente leitura.  
  
 Algumas situações comuns em que um arquivo fica aberto exclusivamente são quando:  
  
- O aplicativo está em execução e usando os arquivos dele. Para resolver esse problema, verifique se o aplicativo não está em execução.  
  
- Outro aplicativo abriu o arquivo. Para resolver esse problema, verifique se nenhum outro aplicativo está acessando os arquivos. Nem sempre é óbvio qual aplicativo está acessando seus arquivos. Nesse caso, reiniciar o computador pode ser o caminho mais fácil para encerrar o aplicativo.  
  
 Se apenas um dos arquivos de saída do projeto estiver marcado como somente leitura, esta exceção será acionada.  
  
 **ID do erro:** BC31019  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Compile o programa novamente para verificar se o erro persiste.  
  
2. Se o erro persistir, salve seu trabalho e reinicie o Visual Studio.  
  
3. Se o erro persistir, reinicie o computador.  
  
4. Se o erro persistir, reinstale o Visual Basic.  
  
5. Se o erro persistir após a reinstalação, notifique o Microsoft Product Support Services.  
  
### <a name="to-check-file-attributes-in-file-explorer"></a>Para verificar atributos de arquivo no Explorador de Arquivos  
  
1. Abra a pasta que lhe interessa.  
  
2. Clique o **modos de exibição** ícone e escolha **detalhes**.  
  
3. Clique com botão direito no cabeçalho da coluna e, em seguida, escolha **atributos** na lista suspensa.  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a>Para alterar os atributos de um arquivo ou pasta  
  
1. Na **Explorador de arquivos**, clique com botão direito no arquivo ou pasta e escolha **propriedades**.  
  
2. No **atributos** seção o **gerais** guia, desmarque o **somente leitura** caixa.  
  
3. Pressione **OK**.  
  
## <a name="see-also"></a>Consulte também

- [Fale conosco](/visualstudio/ide/talk-to-us)
