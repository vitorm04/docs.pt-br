---
title: Aplicativos de 64 bits
ms.date: 03/30/2017
helpviewer_keywords:
- applications [C++], 64-bit
- 64-bit applications [C++]
- 64-bit programming [C++]
ms.assetid: fd4026bc-2c3d-4b27-86dc-ec5e96018181
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fe12f67814b2fc049ec26c745b43aa85627d555
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744269"
---
# <a name="64-bit-applications"></a>Aplicativos de 64 bits
Ao compilar um aplicativo, você pode especificar se ele deve ser executado em um sistema operacional Windows de 64 bits como um aplicativo nativo ou no WOW64 (Windows de 32 bits em Windows de 64 bits). O WOW64 é um ambiente de compatibilidade que permite que um aplicativo de 32 bits seja executado em um sistema de 64 bits. O WOW64 está incluído em todas as versões de 64 bits do sistema operacional Windows.  
  
## <a name="running-32-bit-vs-64-bit-applications-on-windows"></a>Executando aplicativos de 32 bits vs. de 64 bits no Windows  
 Todos os aplicativos criados no .NET Framework 1.0 ou 1.1 são tratados como aplicativos de 32 bits em um sistema operacional de 64 bits e são sempre executados no WOW64 e no CLR (Common Language Runtime) de 32 bits. Os aplicativos de 32 bits que são criados no [!INCLUDE[net_v40_long](../../includes/net-v40-long-md.md)] ou versões posteriores também são executados no WOW64 em sistemas de 64 bits.  
  
 O Visual Studio instala a versão de 32 bits do CLR em um computador x86, e a versão de 32 bits e a versão de 64 bits apropriada do CLR em um computador Windows de 64 bits. (Como o Visual Studio é um aplicativo de 32 bits, quando ele é instalado em um sistema de 64 bits, ele é executado no WOW64.)  
  
> [!NOTE]
>  Em razão do projeto da emulação do x86 e do subsistema do WOW64 para a família de processadores Itanium, os aplicativos são restritos à execução em um processador. Esses fatores reduzem o desempenho e escalabilidade de aplicativos do .NET Framework de 32 bits executados em sistemas baseados em Itanium. É recomendável usar o [!INCLUDE[net_v40_long](../../includes/net-v40-long-md.md)], que inclui suporte nativo para sistemas baseados em Itanium de 64 bits, para aumento de desempenho e escalabilidade.  
  
 Por padrão, ao executar um aplicativo gerenciado de 64 bits em um sistema operacional Windows de 64 bits, você pode criar um objeto que não ultrapasse 2 GB. No entanto, no [!INCLUDE[net_v45](../../includes/net-v45-md.md)], você pode aumentar esse limite.  Para saber mais, confira o [\<elemento gcAllowVeryLargeObjects>](../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md).  
  
 Muitos assemblies são executados de modo idêntico no CLR de 32 bits e no CLR de 64 bits. No entanto, alguns programas podem se comportar de maneira diferente, dependendo do CLR, se eles contiverem um ou mais dos seguintes itens:  
  
-   Estruturas que contêm membros que alteram o tamanho de acordo com a plataforma (por exemplo, qualquer tipo de ponteiro).  
  
-   Aritmética de ponteiro que inclui tamanhos constantes.  
  
-   As declarações COM ou de invocação de plataforma incorreta que usam `Int32` para identificadores em vez de `IntPtr`.  
  
-   Código que converte `IntPtr` em `Int32`.  
  
 Para obter mais informações sobre como portar um aplicativo de 32 bits para execução no CLR de 64 bits, consulte [Migrando um código gerenciado de 32 bits para 64 bits](https://msdn.microsoft.com/library/ms973190.aspx).  
  
## <a name="general-64-bit-programming-information"></a>Informações de Programação em 64 Bits em Geral  
 Para obter informações gerais sobre a programação de 64 bits, confira os seguintes documentos:  
  
-   Para saber mais sobre a versão de 64 bits do CLR em um computador Windows de 64 bits, confira [.NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=37079) (Central de Desenvolvedores do .NET Framework) no site do MSDN.  
  
-   Na documentação do [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)], confira [Programming Guide for 64-bit Windows](http://go.microsoft.com/fwlink/p/?LinkId=253512) (Guia de programação para Windows de 64 bits).  
  
-   Para saber mais sobre como baixar uma versão de 64 bits do CLR, confira [.NET Framework Developer Center Downloads](http://go.microsoft.com/fwlink/?LinkId=50953) (Downloads da Central de desenvolvedores do .NET Framework) no site do MSDN.  
  
-   Para saber mais sobre o suporte do Visual Studio para criar aplicativos de 64 bits, confira [Visual Studio IDE 64-Bit Support](http://msdn.microsoft.com/library/b08ff3ad-c6fd-468f-94d5-01a61aab6833) (Suporte ao IDE do Visual Studio de 64 bits).  
  
## <a name="compiler-support-for-creating-64-bit-applications"></a>Suporte do Compilador para Criar Aplicativos de 64 Bits  
 Por padrão, quando você usa o .NET Framework para criar um aplicativo em um computador de 32 bits ou 64 bits, o aplicativo será executado em um computador de 64 bits como um aplicativo nativo (isto é, não no WOW64). A tabela a seguir lista os documentos que explicam como usar compiladores do Visual Studio para criar aplicativos de 64 bits que serão executados como nativos, no WOW64, ou em ambos.  
  
|Compilador|Opção de compilador|  
|--------------|---------------------|  
|Visual Basic|[/platform (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/platform.md)|  
|Visual C#|[/platform (Opções de compilador do C#)](~/docs/csharp/language-reference/compiler-options/platform-compiler-option.md)|  
|Visual C++|Você pode criar aplicativos MSIL (Microsoft Intermediate Language) independentes de plataforma usando **/clr:safe**. Para obter mais informações, consulte [/clr (compilação de Common Language Runtime)](/cpp/build/reference/clr-common-language-runtime-compilation).<br /><br /> O Visual C++ inclui um compilador separado para cada sistema operacional de 64 bits. Para saber mais sobre como usar o Visual C++ para criar aplicativos nativos que são executados em um sistema operacional Windows de 64 bits, confira [Programação de 64 bits](http://msdn.microsoft.com/library/h2k70f3s\(v=vs.80\)).|  
  
## <a name="determining-the-status-of-an-exe-file-or-dll-file"></a>Determinando o Status de um Arquivo .exe ou .dll  
 Para determinar se um arquivo .exe ou .dll deve ser executado apenas em uma plataforma específica ou no WOW64, use [CorFlags.exe (Ferramenta de Conversão CorFlags)](../../docs/framework/tools/corflags-exe-corflags-conversion-tool.md) sem opções. Você também pode usar CorFlags.exe para alterar o status da plataforma de um arquivo .exe ou .dll. O cabeçalho CLR de um assembly do Visual Studio tem o número de versão principal do tempo de execução definido como 2 e o número de versão secundário do tempo de execução definido como 5. Os aplicativos que têm a versão secundária do tempo de execução definida como 0 são tratados como aplicativos herdados e são sempre executados no WOW64.  
  
 Para consultar programaticamente um .exe ou .dll para saber se ele deve ser executado somente em uma plataforma específica ou no WOW64, use o método <xref:System.Reflection.Module.GetPEKind%2A?displayProperty=nameWithType>.
