---
title: Facilitando a depuração no .NET de uma imagem
description: Saiba como configurar uma imagem executável para depuração mais fácil usando o IDE muda e opções de linha de comando.
ms.date: 08/30/2018
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f25eaaa17d4c4bd2e9522591bb0fd66445cdb6f
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46710716"
---
# <a name="making-an-image-easier-to-debug-in-net"></a>Facilitando a depuração no .NET de uma imagem

Ao compilar código não gerenciado, você pode configurar uma imagem executável para depuração, definindo opções de IDE ou opções de linha de comando. Por exemplo, você pode usar a opção de linha de comando /**Zi** no Visual C++ para solicitar a ele que emita arquivos de símbolo de depuração (extensão de arquivo .pdb). De modo similar, a opção de linha de comando /**Od** informa ao compilador para desabilitar a otimização. O código resultante é executado mais lentamente, mas é mais fácil de depurar, se isso for necessário.

Quando a compilação do .NET Framework, código gerenciado, compiladores como Visual C++, Visual Basic e c# compilar seu programa de origem em Microsoft intermediate language (MSIL). MSIL, em seguida, é compilado em JIT, logo antes da execução, código de máquina nativo. Assim como ocorre com código não gerenciado, você pode configurar uma imagem executável para depuração, definindo opções de IDE ou opções de linha de comando. Você também pode configurar a compilação JIT para depuração da mesma forma.

Essa configuração de JIT tem dois aspectos:

- Você pode solicitar que o compilador JIT para gerar informações de acompanhamento. Isso possibilita que o depurador faça a correspondência entre uma cadeia de MSIL com seu equivalente em código de máquina e que controle o local em que os argumentos de função e variáveis locais são armazenados. Começando com o .NET Framework versão 2.0, o compilador JIT sempre gera informações de acompanhamento, portanto, não há nenhuma necessidade de solicitar a ele.

- Você pode solicitar que o compilador JIT não Otimize o código de máquina resultante.

Normalmente, o compilador que gera o MSIL define essas opções do compilador JIT adequadamente, com base nas opções IDE ou opções de linha de comando que você especificar, por exemplo, /**Od**.

Em alguns casos, talvez você queira alterar o comportamento do compilador JIT para que o código de máquina gerado por ele seja mais fácil de depurar. Por exemplo, talvez você queira gerar informações de acompanhamento JIT de um build de varejo ou controlar a otimização. Você pode fazer isso com um arquivo de inicialização (.ini).

Por exemplo, se o assembly que você deseja depurar é chamado *MyApp.exe*, em seguida, você pode criar um arquivo de texto chamado *MyApp*, na mesma pasta do *MyApp.exe*, que contém Estas três linhas:

```txt
[.NET Framework Debugging Control]
GenerateTrackingInfo=1
AllowOptimize=0
```

Você pode definir o valor de cada opção como 0 ou 1 e qualquer opção ausente assume 0 por padrão. Configurar `GenerateTrackingInfo` como 1 e `AllowOptimize` como 0 proporciona a depuração mais fácil.

Começando com o .NET Framework versão 2.0, o compilador JIT sempre gera informações de acompanhamento, independentemente do valor de `GenerateTrackingInfo`; no entanto, o `AllowOptimize` valor ainda tem um efeito. Ao usar o [Ngen.exe (Gerador de Imagens Nativas)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) para pré-compilar a imagem nativa sem otimização, o arquivo .ini deve estar presente na pasta de destino com `AllowOptimize=0` quando Ngen.exe for executado. Se você tiver pré-compilado um assembly sem otimização, você deve remover o código pré-compilado usando NGen.exe **/uninstall** opção antes de executar novamente o Ngen.exe para pré-compilar o código como otimizado. Se o arquivo. ini não estiver presente na pasta, por padrão Ngen.exe pré-compilará o código como otimizado.

O <xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> controla as configurações de um assembly. **DebuggableAttribute** inclui dois campos que controlam se o compilador JIT deve otimizar e/ou gerar informações de acompanhamento. Começando com o .NET Framework versão 2.0, o compilador JIT sempre gera informações de acompanhamento.

Para um build de varejo, os compiladores não definir qualquer **DebuggableAttribute**. Por padrão, o compilador JIT gera o melhor desempenho, mais difícil de depurar o código de máquina. Habilitar o acompanhamento JIT reduz um pouco o desempenho, enquanto desabilitar a otimização reduz muito o desempenho.

O **DebuggableAttribute** aplica-se a um assembly inteiro por vez e não a módulos individuais dentro do assembly. Ferramentas de desenvolvimento, portanto, deverão anexar atributos personalizados ao token de metadados de assembly se um assembly já tiver sido criado ou então anexá-los à classe chamada **System.Runtime.CompilerServices.AssemblyAttributesGoHere**. A ferramenta ALink promoverá esses **DebuggableAttribute** atributos de cada módulo ao assembly que eles se tornam parte do. Se houver um conflito, a operação ALink falhará.

> [!NOTE]
> Na versão 1.0 do .NET Framework, o compilador do Microsoft Visual C++ adiciona o **DebuggableAttribute** quando as opções do compilador **/clr** e **/Zi** são especificadas. Na versão 1.1 do .NET Framework, você deverá adicionar o **DebugabbleAttribute** manualmente no seu código ou usar a opção de vinculador **/ASSEMBLYDEBUG**.

## <a name="see-also"></a>Consulte também

- [Depuração, rastreamento e criação de perfil](../../../docs/framework/debug-trace-profile/index.md)
- [Habilitando a depuração por anexação JIT](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)
- [Habilitando a criação de perfil](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s5ec0es1(v=vs.100))
