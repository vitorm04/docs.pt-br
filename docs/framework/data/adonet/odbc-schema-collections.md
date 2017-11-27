---
title: "Coleções de esquema ODBC"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 889e84db39af1257d709ef049e18d4397ea700d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="fce5b-102">Coleções de esquema ODBC</span><span class="sxs-lookup"><span data-stu-id="fce5b-102">ODBC Schema Collections</span></span>
<span data-ttu-id="fce5b-103">Esta seção discute o suporte de coleção de esquema para os drivers ODBC para Microsoft SQL Server, Oracle e Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="fce5b-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="fce5b-104">Driver ODBC do Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="fce5b-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="fce5b-105">O Driver ODBC do Microsoft SQL Server suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="fce5b-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="fce5b-106">Tabelas</span><span class="sxs-lookup"><span data-stu-id="fce5b-106">Tables</span></span>  
  
-   <span data-ttu-id="fce5b-107">Índices</span><span class="sxs-lookup"><span data-stu-id="fce5b-107">Indexes</span></span>  
  
-   <span data-ttu-id="fce5b-108">Colunas</span><span class="sxs-lookup"><span data-stu-id="fce5b-108">Columns</span></span>  
  
-   <span data-ttu-id="fce5b-109">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="fce5b-109">Procedures</span></span>  
  
-   <span data-ttu-id="fce5b-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="fce5b-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="fce5b-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="fce5b-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="fce5b-112">Exibições</span><span class="sxs-lookup"><span data-stu-id="fce5b-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="fce5b-113">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="fce5b-113">Tables and Views</span></span>  
  
|<span data-ttu-id="fce5b-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="fce5b-114">ColumnName</span></span>|<span data-ttu-id="fce5b-115">DataType</span><span class="sxs-lookup"><span data-stu-id="fce5b-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="fce5b-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="fce5b-116">TABLE_CAT</span></span>|<span data-ttu-id="fce5b-117">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-117">String</span></span>|  
|<span data-ttu-id="fce5b-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="fce5b-118">TABLE_SCHEM</span></span>|<span data-ttu-id="fce5b-119">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-119">String</span></span>|  
|<span data-ttu-id="fce5b-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-120">TABLE_NAME</span></span>|<span data-ttu-id="fce5b-121">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-121">String</span></span>|  
|<span data-ttu-id="fce5b-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-122">TABLE_TYPE</span></span>|<span data-ttu-id="fce5b-123">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-123">String</span></span>|  
|<span data-ttu-id="fce5b-124">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="fce5b-124">REMARKS</span></span>|<span data-ttu-id="fce5b-125">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="fce5b-126">Índices</span><span class="sxs-lookup"><span data-stu-id="fce5b-126">Indexes</span></span>  
  
|<span data-ttu-id="fce5b-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="fce5b-127">ColumnName</span></span>|<span data-ttu-id="fce5b-128">DataType</span><span class="sxs-lookup"><span data-stu-id="fce5b-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="fce5b-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="fce5b-129">TABLE_CAT</span></span>|<span data-ttu-id="fce5b-130">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-130">String</span></span>|  
|<span data-ttu-id="fce5b-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="fce5b-131">TABLE_SCHEM</span></span>|<span data-ttu-id="fce5b-132">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-132">String</span></span>|  
|<span data-ttu-id="fce5b-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-133">TABLE_NAME</span></span>|<span data-ttu-id="fce5b-134">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-134">String</span></span>|  
|<span data-ttu-id="fce5b-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="fce5b-135">NON_UNIQUE</span></span>|<span data-ttu-id="fce5b-136">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-136">Int16</span></span>|  
|<span data-ttu-id="fce5b-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="fce5b-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="fce5b-138">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-138">String</span></span>|  
|<span data-ttu-id="fce5b-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-139">INDEX_NAME</span></span>|<span data-ttu-id="fce5b-140">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-140">String</span></span>|  
|<span data-ttu-id="fce5b-141">TIPO DE</span><span class="sxs-lookup"><span data-stu-id="fce5b-141">TYPE</span></span>|<span data-ttu-id="fce5b-142">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-142">Int16</span></span>|  
|<span data-ttu-id="fce5b-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="fce5b-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="fce5b-144">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-144">Int16</span></span>|  
|<span data-ttu-id="fce5b-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-145">COLUMN_NAME</span></span>|<span data-ttu-id="fce5b-146">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-146">String</span></span>|  
|<span data-ttu-id="fce5b-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="fce5b-147">ASC_OR_DESC</span></span>|<span data-ttu-id="fce5b-148">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-148">String</span></span>|  
|<span data-ttu-id="fce5b-149">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="fce5b-149">CARDINATLITY</span></span>|<span data-ttu-id="fce5b-150">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-150">Int32</span></span>|  
|<span data-ttu-id="fce5b-151">PÁGINAS</span><span class="sxs-lookup"><span data-stu-id="fce5b-151">PAGES</span></span>|<span data-ttu-id="fce5b-152">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-152">Int32</span></span>|  
|<span data-ttu-id="fce5b-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="fce5b-153">FILTER_CONDITION</span></span>|<span data-ttu-id="fce5b-154">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-154">String</span></span>|  
|<span data-ttu-id="fce5b-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="fce5b-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="fce5b-156">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-156">String</span></span>|  
|<span data-ttu-id="fce5b-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="fce5b-158">Byte</span><span class="sxs-lookup"><span data-stu-id="fce5b-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="fce5b-159">Colunas</span><span class="sxs-lookup"><span data-stu-id="fce5b-159">Columns</span></span>  
  
|<span data-ttu-id="fce5b-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="fce5b-160">ColumnName</span></span>|<span data-ttu-id="fce5b-161">DataType</span><span class="sxs-lookup"><span data-stu-id="fce5b-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="fce5b-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="fce5b-162">TABLE_CAT</span></span>|<span data-ttu-id="fce5b-163">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-163">String</span></span>|  
|<span data-ttu-id="fce5b-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="fce5b-164">TABLE_SCHEM</span></span>|<span data-ttu-id="fce5b-165">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-165">String</span></span>|  
|<span data-ttu-id="fce5b-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-166">TABLE_NAME</span></span>|<span data-ttu-id="fce5b-167">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-167">String</span></span>|  
|<span data-ttu-id="fce5b-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-168">COLUMN_NAME</span></span>|<span data-ttu-id="fce5b-169">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-169">String</span></span>|  
|<span data-ttu-id="fce5b-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-170">DATA_TYPE</span></span>|<span data-ttu-id="fce5b-171">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-171">Int16</span></span>|  
|<span data-ttu-id="fce5b-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-172">TYPE_NAME</span></span>|<span data-ttu-id="fce5b-173">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-173">String</span></span>|  
|<span data-ttu-id="fce5b-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="fce5b-174">COLUMN_SIZE</span></span>|<span data-ttu-id="fce5b-175">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-175">Int32</span></span>|  
|<span data-ttu-id="fce5b-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="fce5b-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="fce5b-177">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-177">Int32</span></span>|  
|<span data-ttu-id="fce5b-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="fce5b-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="fce5b-179">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-179">Int16</span></span>|  
|<span data-ttu-id="fce5b-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="fce5b-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="fce5b-181">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-181">Int16</span></span>|  
|<span data-ttu-id="fce5b-182">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="fce5b-182">NULLABLE</span></span>|<span data-ttu-id="fce5b-183">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-183">Int16</span></span>|  
|<span data-ttu-id="fce5b-184">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="fce5b-184">REMARKS</span></span>|<span data-ttu-id="fce5b-185">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-185">String</span></span>|  
|<span data-ttu-id="fce5b-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="fce5b-186">COLUMN_DEF</span></span>|<span data-ttu-id="fce5b-187">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-187">String</span></span>|  
|<span data-ttu-id="fce5b-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="fce5b-189">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-189">Int16</span></span>|  
|<span data-ttu-id="fce5b-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="fce5b-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="fce5b-191">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-191">Int16</span></span>|  
|<span data-ttu-id="fce5b-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="fce5b-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="fce5b-193">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-193">Int32</span></span>|  
|<span data-ttu-id="fce5b-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="fce5b-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="fce5b-195">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-195">Int32</span></span>|  
|<span data-ttu-id="fce5b-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="fce5b-196">IS_NULLABLE</span></span>|<span data-ttu-id="fce5b-197">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-197">String</span></span>|  
|<span data-ttu-id="fce5b-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="fce5b-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="fce5b-199">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-199">String</span></span>|  
|<span data-ttu-id="fce5b-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="fce5b-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="fce5b-201">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-201">String</span></span>|  
|<span data-ttu-id="fce5b-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="fce5b-203">Byte</span><span class="sxs-lookup"><span data-stu-id="fce5b-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="fce5b-204">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="fce5b-204">Procedures</span></span>  
  
|<span data-ttu-id="fce5b-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="fce5b-205">ColumnName</span></span>|<span data-ttu-id="fce5b-206">DataType</span><span class="sxs-lookup"><span data-stu-id="fce5b-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="fce5b-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="fce5b-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="fce5b-208">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-208">String</span></span>|  
|<span data-ttu-id="fce5b-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="fce5b-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="fce5b-210">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-210">String</span></span>|  
|<span data-ttu-id="fce5b-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="fce5b-212">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-212">String</span></span>|  
|<span data-ttu-id="fce5b-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="fce5b-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="fce5b-214">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-214">Int32</span></span>|  
|<span data-ttu-id="fce5b-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="fce5b-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="fce5b-216">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-216">Int32</span></span>|  
|<span data-ttu-id="fce5b-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="fce5b-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="fce5b-218">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-218">Int32</span></span>|  
|<span data-ttu-id="fce5b-219">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="fce5b-219">REMARKS</span></span>|<span data-ttu-id="fce5b-220">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-220">String</span></span>|  
|<span data-ttu-id="fce5b-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="fce5b-222">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="fce5b-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="fce5b-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="fce5b-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="fce5b-224">ColumnName</span></span>|<span data-ttu-id="fce5b-225">DataType</span><span class="sxs-lookup"><span data-stu-id="fce5b-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="fce5b-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="fce5b-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="fce5b-227">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-227">String</span></span>|  
|<span data-ttu-id="fce5b-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="fce5b-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="fce5b-229">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-229">String</span></span>|  
|<span data-ttu-id="fce5b-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="fce5b-231">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-231">String</span></span>|  
|<span data-ttu-id="fce5b-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-232">COLUMN_NAME</span></span>|<span data-ttu-id="fce5b-233">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-233">String</span></span>|  
|<span data-ttu-id="fce5b-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-234">COLUMN_TYPE</span></span>|<span data-ttu-id="fce5b-235">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-235">Int16</span></span>|  
|<span data-ttu-id="fce5b-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-236">DATA_TYPE</span></span>|<span data-ttu-id="fce5b-237">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-237">Int16</span></span>|  
|<span data-ttu-id="fce5b-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-238">TYPE_NAME</span></span>|<span data-ttu-id="fce5b-239">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-239">String</span></span>|  
|<span data-ttu-id="fce5b-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="fce5b-240">COLUMN_SIZE</span></span>|<span data-ttu-id="fce5b-241">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-241">Int32</span></span>|  
|<span data-ttu-id="fce5b-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="fce5b-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="fce5b-243">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-243">Int32</span></span>|  
|<span data-ttu-id="fce5b-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="fce5b-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="fce5b-245">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-245">Int16</span></span>|  
|<span data-ttu-id="fce5b-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="fce5b-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="fce5b-247">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-247">Int16</span></span>|  
|<span data-ttu-id="fce5b-248">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="fce5b-248">NULLABLE</span></span>|<span data-ttu-id="fce5b-249">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-249">Int16</span></span>|  
|<span data-ttu-id="fce5b-250">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="fce5b-250">REMARKS</span></span>|<span data-ttu-id="fce5b-251">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-251">String</span></span>|  
|<span data-ttu-id="fce5b-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="fce5b-252">COLUMN_DEF</span></span>|<span data-ttu-id="fce5b-253">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-253">String</span></span>|  
|<span data-ttu-id="fce5b-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="fce5b-255">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-255">Int16</span></span>|  
|<span data-ttu-id="fce5b-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="fce5b-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="fce5b-257">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-257">Int16</span></span>|  
|<span data-ttu-id="fce5b-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="fce5b-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="fce5b-259">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-259">Int32</span></span>|  
|<span data-ttu-id="fce5b-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="fce5b-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="fce5b-261">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-261">Int32</span></span>|  
|<span data-ttu-id="fce5b-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="fce5b-262">IS_NULLABLE</span></span>|<span data-ttu-id="fce5b-263">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-263">String</span></span>|  
|<span data-ttu-id="fce5b-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="fce5b-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="fce5b-265">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-265">String</span></span>|  
|<span data-ttu-id="fce5b-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="fce5b-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="fce5b-267">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-267">String</span></span>|  
|<span data-ttu-id="fce5b-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="fce5b-269">Byte</span><span class="sxs-lookup"><span data-stu-id="fce5b-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="fce5b-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="fce5b-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="fce5b-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="fce5b-271">ColumnName</span></span>|<span data-ttu-id="fce5b-272">DataType</span><span class="sxs-lookup"><span data-stu-id="fce5b-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="fce5b-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="fce5b-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="fce5b-274">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-274">String</span></span>|  
|<span data-ttu-id="fce5b-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="fce5b-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="fce5b-276">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-276">String</span></span>|  
|<span data-ttu-id="fce5b-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="fce5b-278">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-278">String</span></span>|  
|<span data-ttu-id="fce5b-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-279">COLUMN_NAME</span></span>|<span data-ttu-id="fce5b-280">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-280">String</span></span>|  
|<span data-ttu-id="fce5b-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-281">COLUMN_TYPE</span></span>|<span data-ttu-id="fce5b-282">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-282">Int16</span></span>|  
|<span data-ttu-id="fce5b-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-283">DATA_TYPE</span></span>|<span data-ttu-id="fce5b-284">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-284">Int16</span></span>|  
|<span data-ttu-id="fce5b-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-285">TYPE_NAME</span></span>|<span data-ttu-id="fce5b-286">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-286">String</span></span>|  
|<span data-ttu-id="fce5b-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="fce5b-287">COLUMN_SIZE</span></span>|<span data-ttu-id="fce5b-288">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-288">Int32</span></span>|  
|<span data-ttu-id="fce5b-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="fce5b-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="fce5b-290">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-290">Int32</span></span>|  
|<span data-ttu-id="fce5b-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="fce5b-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="fce5b-292">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-292">Int16</span></span>|  
|<span data-ttu-id="fce5b-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="fce5b-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="fce5b-294">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-294">Int16</span></span>|  
|<span data-ttu-id="fce5b-295">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="fce5b-295">NULLABLE</span></span>|<span data-ttu-id="fce5b-296">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-296">Int16</span></span>|  
|<span data-ttu-id="fce5b-297">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="fce5b-297">REMARKS</span></span>|<span data-ttu-id="fce5b-298">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-298">String</span></span>|  
|<span data-ttu-id="fce5b-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="fce5b-299">COLUMN_DEF</span></span>|<span data-ttu-id="fce5b-300">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-300">String</span></span>|  
|<span data-ttu-id="fce5b-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="fce5b-302">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-302">Int16</span></span>|  
|<span data-ttu-id="fce5b-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="fce5b-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="fce5b-304">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-304">Int16</span></span>|  
|<span data-ttu-id="fce5b-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="fce5b-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="fce5b-306">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-306">Int32</span></span>|  
|<span data-ttu-id="fce5b-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="fce5b-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="fce5b-308">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-308">Int32</span></span>|  
|<span data-ttu-id="fce5b-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="fce5b-309">IS_NULLABLE</span></span>|<span data-ttu-id="fce5b-310">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-310">String</span></span>|  
|<span data-ttu-id="fce5b-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="fce5b-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="fce5b-312">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-312">String</span></span>|  
|<span data-ttu-id="fce5b-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="fce5b-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="fce5b-314">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-314">String</span></span>|  
|<span data-ttu-id="fce5b-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="fce5b-316">Byte</span><span class="sxs-lookup"><span data-stu-id="fce5b-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="fce5b-317">Driver ODBC do Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="fce5b-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="fce5b-318">O Driver ODBC do Microsoft SQL Server Oracle suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="fce5b-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="fce5b-319">Tabelas</span><span class="sxs-lookup"><span data-stu-id="fce5b-319">Tables</span></span>  
  
-   <span data-ttu-id="fce5b-320">Colunas</span><span class="sxs-lookup"><span data-stu-id="fce5b-320">Columns</span></span>  
  
-   <span data-ttu-id="fce5b-321">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="fce5b-321">Procedures</span></span>  
  
-   <span data-ttu-id="fce5b-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="fce5b-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="fce5b-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="fce5b-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="fce5b-324">Exibições</span><span class="sxs-lookup"><span data-stu-id="fce5b-324">Views</span></span>  
  
-   <span data-ttu-id="fce5b-325">Índices</span><span class="sxs-lookup"><span data-stu-id="fce5b-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="fce5b-326">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="fce5b-326">Tables and Views</span></span>  
  
|<span data-ttu-id="fce5b-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="fce5b-327">ColumnName</span></span>|<span data-ttu-id="fce5b-328">DataType</span><span class="sxs-lookup"><span data-stu-id="fce5b-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="fce5b-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="fce5b-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="fce5b-330">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-330">String</span></span>|  
|<span data-ttu-id="fce5b-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="fce5b-331">TABLE_OWNER</span></span>|<span data-ttu-id="fce5b-332">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-332">String</span></span>|  
|<span data-ttu-id="fce5b-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-333">TABLE_NAME</span></span>|<span data-ttu-id="fce5b-334">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-334">String</span></span>|  
|<span data-ttu-id="fce5b-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-335">TABLE_TYPE</span></span>|<span data-ttu-id="fce5b-336">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-336">String</span></span>|  
|<span data-ttu-id="fce5b-337">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="fce5b-337">REMARKS</span></span>|<span data-ttu-id="fce5b-338">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="fce5b-339">Colunas</span><span class="sxs-lookup"><span data-stu-id="fce5b-339">Columns</span></span>  
  
|<span data-ttu-id="fce5b-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="fce5b-340">ColumnName</span></span>|<span data-ttu-id="fce5b-341">DataType</span><span class="sxs-lookup"><span data-stu-id="fce5b-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="fce5b-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="fce5b-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="fce5b-343">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-343">String</span></span>|  
|<span data-ttu-id="fce5b-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="fce5b-344">TABLE_OWNER</span></span>|<span data-ttu-id="fce5b-345">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-345">String</span></span>|  
|<span data-ttu-id="fce5b-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-346">TABLE_NAME</span></span>|<span data-ttu-id="fce5b-347">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-347">String</span></span>|  
|<span data-ttu-id="fce5b-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-348">COLUMN_NAME</span></span>|<span data-ttu-id="fce5b-349">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-349">String</span></span>|  
|<span data-ttu-id="fce5b-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-350">DATA_TYPE</span></span>|<span data-ttu-id="fce5b-351">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-351">Int16</span></span>|  
|<span data-ttu-id="fce5b-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-352">TYPE_NAME</span></span>|<span data-ttu-id="fce5b-353">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-353">String</span></span>|  
|<span data-ttu-id="fce5b-354">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="fce5b-354">PRECISION</span></span>|<span data-ttu-id="fce5b-355">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-355">Int32</span></span>|  
|<span data-ttu-id="fce5b-356">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="fce5b-356">LENGTH</span></span>|<span data-ttu-id="fce5b-357">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-357">Int32</span></span>|  
|<span data-ttu-id="fce5b-358">ESCALA</span><span class="sxs-lookup"><span data-stu-id="fce5b-358">SCALE</span></span>|<span data-ttu-id="fce5b-359">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-359">Int16</span></span>|  
|<span data-ttu-id="fce5b-360">BASE</span><span class="sxs-lookup"><span data-stu-id="fce5b-360">RADIX</span></span>|<span data-ttu-id="fce5b-361">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-361">Int16</span></span>|  
|<span data-ttu-id="fce5b-362">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="fce5b-362">NULLABLE</span></span>|<span data-ttu-id="fce5b-363">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-363">Int16</span></span>|  
|<span data-ttu-id="fce5b-364">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="fce5b-364">REMARKS</span></span>|<span data-ttu-id="fce5b-365">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-365">String</span></span>|  
|<span data-ttu-id="fce5b-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="fce5b-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="fce5b-367">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="fce5b-368">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="fce5b-368">Procedures</span></span>  
  
|<span data-ttu-id="fce5b-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="fce5b-369">ColumnName</span></span>|<span data-ttu-id="fce5b-370">DataType</span><span class="sxs-lookup"><span data-stu-id="fce5b-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="fce5b-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="fce5b-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="fce5b-372">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-372">String</span></span>|  
|<span data-ttu-id="fce5b-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="fce5b-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="fce5b-374">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-374">String</span></span>|  
|<span data-ttu-id="fce5b-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="fce5b-376">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-376">String</span></span>|  
|<span data-ttu-id="fce5b-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="fce5b-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="fce5b-378">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-378">Int16</span></span>|  
|<span data-ttu-id="fce5b-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="fce5b-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="fce5b-380">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-380">Int16</span></span>|  
|<span data-ttu-id="fce5b-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="fce5b-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="fce5b-382">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-382">Int16</span></span>|  
|<span data-ttu-id="fce5b-383">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="fce5b-383">REMARKS</span></span>|<span data-ttu-id="fce5b-384">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-384">String</span></span>|  
|<span data-ttu-id="fce5b-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="fce5b-386">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="fce5b-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="fce5b-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="fce5b-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="fce5b-388">ColumnName</span></span>|<span data-ttu-id="fce5b-389">DataType</span><span class="sxs-lookup"><span data-stu-id="fce5b-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="fce5b-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="fce5b-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="fce5b-391">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-391">String</span></span>|  
|<span data-ttu-id="fce5b-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="fce5b-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="fce5b-393">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-393">String</span></span>|  
|<span data-ttu-id="fce5b-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="fce5b-395">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-395">String</span></span>|  
|<span data-ttu-id="fce5b-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-396">COLUMN_NAME</span></span>|<span data-ttu-id="fce5b-397">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-397">String</span></span>|  
|<span data-ttu-id="fce5b-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-398">COLUMN_TYPE</span></span>|<span data-ttu-id="fce5b-399">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-399">Int16</span></span>|  
|<span data-ttu-id="fce5b-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-400">DATA_TYPE</span></span>|<span data-ttu-id="fce5b-401">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-401">Int16</span></span>|  
|<span data-ttu-id="fce5b-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-402">TYPE_NAME</span></span>|<span data-ttu-id="fce5b-403">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-403">String</span></span>|  
|<span data-ttu-id="fce5b-404">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="fce5b-404">PRECISION</span></span>|<span data-ttu-id="fce5b-405">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-405">Int32</span></span>|  
|<span data-ttu-id="fce5b-406">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="fce5b-406">LENGTH</span></span>|<span data-ttu-id="fce5b-407">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-407">Int32</span></span>|  
|<span data-ttu-id="fce5b-408">ESCALA</span><span class="sxs-lookup"><span data-stu-id="fce5b-408">SCALE</span></span>|<span data-ttu-id="fce5b-409">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-409">Int16</span></span>|  
|<span data-ttu-id="fce5b-410">BASE</span><span class="sxs-lookup"><span data-stu-id="fce5b-410">RADIX</span></span>|<span data-ttu-id="fce5b-411">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-411">Int16</span></span>|  
|<span data-ttu-id="fce5b-412">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="fce5b-412">NULLABLE</span></span>|<span data-ttu-id="fce5b-413">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-413">Int16</span></span>|  
|<span data-ttu-id="fce5b-414">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="fce5b-414">REMARKS</span></span>|<span data-ttu-id="fce5b-415">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-415">String</span></span>|  
|<span data-ttu-id="fce5b-416">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="fce5b-416">OVERLOAD</span></span>|<span data-ttu-id="fce5b-417">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-417">Int32</span></span>|  
|<span data-ttu-id="fce5b-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="fce5b-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="fce5b-419">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="fce5b-420">Driver ODBC do Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="fce5b-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="fce5b-421">O Driver de ODBC do Microsoft Jet suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="fce5b-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="fce5b-422">Tabelas</span><span class="sxs-lookup"><span data-stu-id="fce5b-422">Tables</span></span>  
  
-   <span data-ttu-id="fce5b-423">Índices</span><span class="sxs-lookup"><span data-stu-id="fce5b-423">Indexes</span></span>  
  
-   <span data-ttu-id="fce5b-424">Colunas</span><span class="sxs-lookup"><span data-stu-id="fce5b-424">Columns</span></span>  
  
-   <span data-ttu-id="fce5b-425">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="fce5b-425">Procedures</span></span>  
  
-   <span data-ttu-id="fce5b-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="fce5b-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="fce5b-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="fce5b-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="fce5b-428">Exibições</span><span class="sxs-lookup"><span data-stu-id="fce5b-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="fce5b-429">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="fce5b-429">Tables and Views</span></span>  
  
|<span data-ttu-id="fce5b-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="fce5b-430">ColumnName</span></span>|<span data-ttu-id="fce5b-431">DataType</span><span class="sxs-lookup"><span data-stu-id="fce5b-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="fce5b-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="fce5b-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="fce5b-433">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-433">String</span></span>|  
|<span data-ttu-id="fce5b-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="fce5b-434">TABLE_OWNER</span></span>|<span data-ttu-id="fce5b-435">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-435">String</span></span>|  
|<span data-ttu-id="fce5b-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-436">TABLE_NAME</span></span>|<span data-ttu-id="fce5b-437">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-437">String</span></span>|  
|<span data-ttu-id="fce5b-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-438">TABLE_TYPE</span></span>|<span data-ttu-id="fce5b-439">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-439">String</span></span>|  
|<span data-ttu-id="fce5b-440">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="fce5b-440">REMARKS</span></span>|<span data-ttu-id="fce5b-441">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="fce5b-442">Colunas</span><span class="sxs-lookup"><span data-stu-id="fce5b-442">Columns</span></span>  
  
|<span data-ttu-id="fce5b-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="fce5b-443">ColumnName</span></span>|<span data-ttu-id="fce5b-444">DataType</span><span class="sxs-lookup"><span data-stu-id="fce5b-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="fce5b-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="fce5b-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="fce5b-446">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-446">String</span></span>|  
|<span data-ttu-id="fce5b-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="fce5b-447">TABLE_OWNER</span></span>|<span data-ttu-id="fce5b-448">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-448">String</span></span>|  
|<span data-ttu-id="fce5b-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-449">TABLE_NAME</span></span>|<span data-ttu-id="fce5b-450">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-450">String</span></span>|  
|<span data-ttu-id="fce5b-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-451">COLUMN_NAME</span></span>|<span data-ttu-id="fce5b-452">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-452">String</span></span>|  
|<span data-ttu-id="fce5b-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-453">DATA_TYPE</span></span>|<span data-ttu-id="fce5b-454">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-454">Int16</span></span>|  
|<span data-ttu-id="fce5b-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-455">TYPE_NAME</span></span>|<span data-ttu-id="fce5b-456">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-456">String</span></span>|  
|<span data-ttu-id="fce5b-457">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="fce5b-457">PRECISION</span></span>|<span data-ttu-id="fce5b-458">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-458">Int32</span></span>|  
|<span data-ttu-id="fce5b-459">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="fce5b-459">LENGTH</span></span>|<span data-ttu-id="fce5b-460">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-460">Int32</span></span>|  
|<span data-ttu-id="fce5b-461">ESCALA</span><span class="sxs-lookup"><span data-stu-id="fce5b-461">SCALE</span></span>|<span data-ttu-id="fce5b-462">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-462">Int16</span></span>|  
|<span data-ttu-id="fce5b-463">BASE</span><span class="sxs-lookup"><span data-stu-id="fce5b-463">RADIX</span></span>|<span data-ttu-id="fce5b-464">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-464">Int16</span></span>|  
|<span data-ttu-id="fce5b-465">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="fce5b-465">NULLABLE</span></span>|<span data-ttu-id="fce5b-466">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-466">Int16</span></span>|  
|<span data-ttu-id="fce5b-467">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="fce5b-467">REMARKS</span></span>|<span data-ttu-id="fce5b-468">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-468">String</span></span>|  
|<span data-ttu-id="fce5b-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="fce5b-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="fce5b-470">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="fce5b-471">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="fce5b-471">Procedures</span></span>  
  
|<span data-ttu-id="fce5b-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="fce5b-472">ColumnName</span></span>|<span data-ttu-id="fce5b-473">DataType</span><span class="sxs-lookup"><span data-stu-id="fce5b-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="fce5b-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="fce5b-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="fce5b-475">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-475">String</span></span>|  
|<span data-ttu-id="fce5b-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="fce5b-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="fce5b-477">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-477">String</span></span>|  
|<span data-ttu-id="fce5b-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="fce5b-479">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-479">String</span></span>|  
|<span data-ttu-id="fce5b-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="fce5b-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="fce5b-481">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-481">Int16</span></span>|  
|<span data-ttu-id="fce5b-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="fce5b-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="fce5b-483">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-483">Int16</span></span>|  
|<span data-ttu-id="fce5b-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="fce5b-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="fce5b-485">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-485">Int16</span></span>|  
|<span data-ttu-id="fce5b-486">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="fce5b-486">REMARKS</span></span>|<span data-ttu-id="fce5b-487">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-487">String</span></span>|  
|<span data-ttu-id="fce5b-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="fce5b-489">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="fce5b-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="fce5b-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="fce5b-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="fce5b-491">ColumnName</span></span>|<span data-ttu-id="fce5b-492">DataType</span><span class="sxs-lookup"><span data-stu-id="fce5b-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="fce5b-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="fce5b-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="fce5b-494">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-494">String</span></span>|  
|<span data-ttu-id="fce5b-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="fce5b-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="fce5b-496">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-496">String</span></span>|  
|<span data-ttu-id="fce5b-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="fce5b-498">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-498">String</span></span>|  
|<span data-ttu-id="fce5b-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-499">COLUMN_NAME</span></span>|<span data-ttu-id="fce5b-500">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-500">String</span></span>|  
|<span data-ttu-id="fce5b-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-501">COLUMN_TYPE</span></span>|<span data-ttu-id="fce5b-502">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-502">Int16</span></span>|  
|<span data-ttu-id="fce5b-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-503">DATA_TYPE</span></span>|<span data-ttu-id="fce5b-504">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-504">Int16</span></span>|  
|<span data-ttu-id="fce5b-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-505">TYPE_NAME</span></span>|<span data-ttu-id="fce5b-506">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-506">String</span></span>|  
|<span data-ttu-id="fce5b-507">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="fce5b-507">PRECISION</span></span>|<span data-ttu-id="fce5b-508">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-508">Int32</span></span>|  
|<span data-ttu-id="fce5b-509">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="fce5b-509">LENGTH</span></span>|<span data-ttu-id="fce5b-510">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-510">Int32</span></span>|  
|<span data-ttu-id="fce5b-511">ESCALA</span><span class="sxs-lookup"><span data-stu-id="fce5b-511">SCALE</span></span>|<span data-ttu-id="fce5b-512">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-512">Int16</span></span>|  
|<span data-ttu-id="fce5b-513">BASE</span><span class="sxs-lookup"><span data-stu-id="fce5b-513">RADIX</span></span>|<span data-ttu-id="fce5b-514">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-514">Int16</span></span>|  
|<span data-ttu-id="fce5b-515">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="fce5b-515">NULLABLE</span></span>|<span data-ttu-id="fce5b-516">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-516">Int16</span></span>|  
|<span data-ttu-id="fce5b-517">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="fce5b-517">REMARKS</span></span>|<span data-ttu-id="fce5b-518">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-518">String</span></span>|  
|<span data-ttu-id="fce5b-519">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="fce5b-519">OVERLOAD</span></span>|<span data-ttu-id="fce5b-520">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-520">Int32</span></span>|  
|<span data-ttu-id="fce5b-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="fce5b-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="fce5b-522">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="fce5b-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="fce5b-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="fce5b-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="fce5b-524">ColumnName</span></span>|<span data-ttu-id="fce5b-525">DataType</span><span class="sxs-lookup"><span data-stu-id="fce5b-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="fce5b-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="fce5b-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="fce5b-527">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-527">String</span></span>|  
|<span data-ttu-id="fce5b-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="fce5b-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="fce5b-529">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-529">String</span></span>|  
|<span data-ttu-id="fce5b-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="fce5b-531">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-531">String</span></span>|  
|<span data-ttu-id="fce5b-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-532">COLUMN_NAME</span></span>|<span data-ttu-id="fce5b-533">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-533">String</span></span>|  
|<span data-ttu-id="fce5b-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-534">COLUMN_TYPE</span></span>|<span data-ttu-id="fce5b-535">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-535">Int16</span></span>|  
|<span data-ttu-id="fce5b-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-536">DATA_TYPE</span></span>|<span data-ttu-id="fce5b-537">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-537">Int16</span></span>|  
|<span data-ttu-id="fce5b-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="fce5b-538">TYPE_NAME</span></span>|<span data-ttu-id="fce5b-539">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-539">String</span></span>|  
|<span data-ttu-id="fce5b-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="fce5b-540">COLUMN_SIZE</span></span>|<span data-ttu-id="fce5b-541">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-541">Int32</span></span>|  
|<span data-ttu-id="fce5b-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="fce5b-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="fce5b-543">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-543">Int32</span></span>|  
|<span data-ttu-id="fce5b-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="fce5b-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="fce5b-545">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-545">Int16</span></span>|  
|<span data-ttu-id="fce5b-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="fce5b-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="fce5b-547">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-547">Int16</span></span>|  
|<span data-ttu-id="fce5b-548">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="fce5b-548">NULLABLE</span></span>|<span data-ttu-id="fce5b-549">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-549">Int16</span></span>|  
|<span data-ttu-id="fce5b-550">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="fce5b-550">REMARKS</span></span>|<span data-ttu-id="fce5b-551">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-551">String</span></span>|  
|<span data-ttu-id="fce5b-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="fce5b-552">COLUMN_DEF</span></span>|<span data-ttu-id="fce5b-553">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-553">String</span></span>|  
|<span data-ttu-id="fce5b-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="fce5b-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="fce5b-555">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-555">Int16</span></span>|  
|<span data-ttu-id="fce5b-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="fce5b-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="fce5b-557">Int16</span><span class="sxs-lookup"><span data-stu-id="fce5b-557">Int16</span></span>|  
|<span data-ttu-id="fce5b-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="fce5b-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="fce5b-559">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-559">Int32</span></span>|  
|<span data-ttu-id="fce5b-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="fce5b-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="fce5b-561">Int32</span><span class="sxs-lookup"><span data-stu-id="fce5b-561">Int32</span></span>|  
|<span data-ttu-id="fce5b-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="fce5b-562">IS_NULLABLE</span></span>|<span data-ttu-id="fce5b-563">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="fce5b-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fce5b-564">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fce5b-564">See Also</span></span>  
 <span data-ttu-id="fce5b-565">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="fce5b-565">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
