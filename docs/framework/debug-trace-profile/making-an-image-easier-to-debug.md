---
title: Facilitando a depuração de uma imagem
ms.date: 03/30/2017
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c58008bc621ea95fbb2e4cc5e7d4521576aca37c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391040"
---
# <a name="making-an-image-easier-to-debug"></a>Facilitando a depuração de uma imagem
Ao compilar código não gerenciado, você pode configurar uma imagem executável para depuração, definindo opções de IDE ou opções de linha de comando. Por exemplo, você pode usar a opção de linha de comando /**Zi** no Visual C++ para solicitar a ele que emita arquivos de símbolo de depuração (extensão de arquivo .pdb). De modo similar, a opção de linha de comando /**Od** informa ao compilador para desabilitar a otimização. O código resultante é executado mais lentamente, mas é mais fácil depurar, se isso for necessário.  
  
 Ao compilar código gerenciado do .NET Framework, compiladores como Visual C++, Visual Basic e C# compilam seus respectivos programas de origem para MSIL (Microsoft Intermediate Language). A MSIL passa subsequentemente por compilação JIT, logo antes da execução, tornando-se código de máquina nativo. Assim como ocorre com código não gerenciado, você pode configurar uma imagem executável para depuração, definindo opções de IDE ou opções de linha de comando. Além disso, você pode configurar a compilação JIT para depuração da mesma forma.  
  
 Essa configuração de JIT tem dois aspectos:  
  
-   Você pode solicitar que o compilador JIT gere informações de acompanhamento. Isso possibilita que o depurador faça a correspondência entre uma cadeia de MSIL com seu equivalente em código de máquina e que controle o local em que os argumentos de função e variáveis locais são armazenados.  No .NET Framework versão 2.0, o compilador JIT sempre gera informações de acompanhamento, portanto, não é necessário solicitá-las.  
  
-   Você pode solicitar que o compilador JIT não otimize o código de máquina resultante.  
  
 Normalmente, o compilador que gera o MSIL define essas opções do compilador JIT adequadamente com base nas opções IDE ou opções de linha de comando especificadas por você, por exemplo, /**Od**.  
  
 Em alguns casos, talvez você queira alterar o comportamento do compilador JIT para que o código de máquina gerado por ele seja mais fácil de depurar. Por exemplo, talvez você queira gerar informações de acompanhamento JIT de um build de varejo ou controlar a otimização. Você pode fazer isso com um arquivo de inicialização (.ini).  
  
 Por exemplo, se o assembly que você deseja depurar é chamado MyApp.exe, você pode criar, na mesma pasta dele, um arquivo de texto chamado MyApp.ini contendo estas três linhas:  
  
```  
[.NET Framework Debugging Control]  
GenerateTrackingInfo=1  
AllowOptimize=0  
```  
  
 Você pode definir o valor de cada opção como 0 ou 1 e qualquer opção ausente assume 0 por padrão. Configurar `GenerateTrackingInfo` como 1 e `AllowOptimize` como 0 proporciona a depuração mais fácil.  
  
> [!NOTE]
>  No .NET Framework versão 2.0, o compilador JIT sempre gera informações de acompanhamento, independentemente do valor de `GenerateTrackingInfo`; no entanto, o valor de `AllowOptimize` ainda tem um efeito. Ao usar o [Ngen.exe (Gerador de Imagens Nativas)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) para pré-compilar a imagem nativa sem otimização, o arquivo .ini deve estar presente na pasta de destino com `AllowOptimize=0` quando Ngen.exe for executado. Se você tiver pré-compilado um assembly sem otimização, você deverá remover o código pré-compilado usando a opção **/uninstall** do NGen.exe antes de executar novamente o Ngen.exe para pré-compilar o código como otimizado. Se o arquivo .ini não estiver presente na pasta, Ngen.exe pré-compilará o código por padrão como otimizado.  
  
> [!NOTE]
>  O <xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> controla as configurações de um assembly. **DebuggableAttribute** inclui dois campos que registram as configurações que indicam se o compilador JIT deve otimizar e/ou gerar informações de acompanhamento. No .NET Framework versão 2.0, o compilador JIT sempre gera informações de acompanhamento.  
  
> [!NOTE]
>  Para um build de varejo, os compiladores não definem nenhum **DebuggableAttribute**. O comportamento padrão do compilador JIT é gerar o código de máquina com melhor desempenho e mais difícil de depurar. Habilitar o acompanhamento JIT reduz um pouco o desempenho, enquanto desabilitar a otimização reduz muito o desempenho.  
  
> [!NOTE]
>  O **DebuggableAttribute** aplica-se a um assembly inteiro por vez e não a módulos individuais dentro do assembly. Ferramentas de desenvolvimento, portanto, deverão anexar atributos personalizados ao token de metadados de assembly se um assembly já tiver sido criado ou então anexá-los à classe chamada **System.Runtime.CompilerServices.AssemblyAttributesGoHere**. A ferramenta ALink promoverá então esses atributos **DebuggableAttribute** de cada módulo para o assembly do qual eles se tornarão parte. Se houver um conflito, a operação ALink falhará.  
  
> [!NOTE]
>  Na versão 1.0 do .NET Framework, o compilador do Microsoft Visual C++ adiciona o **DebuggableAttribute** quando as opções do compilador **/clr** e **/Zi** são especificadas. Na versão 1.1 do .NET Framework, você deverá adicionar o **DebugabbleAttribute** manualmente no seu código ou usar a opção de vinculador **/ASSEMBLYDEBUG**.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração, rastreamento e criação de perfil](../../../docs/framework/debug-trace-profile/index.md)  
 [Habilitando a depuração por anexação JIT](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 [Habilitando a criação de perfil](http://msdn.microsoft.com/library/3b669676-f0e0-4ebf-8674-68986dd2020d)
