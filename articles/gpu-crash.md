id: gpu-crash
kind: error
title: Erro: a GPU parou de responder (device lost) | Error: the GPU stopped responding (device lost)
keys: gpu parou, gpu travou, device lost, vk_error_device_lost, tela preta, driver reiniciou, placa de video travou, crash da gpu, gpu crash, gpu hang, tdr, nvlddmkm
match: VK_ERROR_DEVICE_LOST
--- pt
A placa de vídeo parou no meio de um quadro e o driver a reiniciou. O editor salva a cena (Salvamento de emergência) e gera um relatório.
- O relatório diz **em que passe a GPU parou** ("A GPU parou no quadro N em “tecido (simulacao)”"): cada passe do quadro é marcado enquanto a GPU trabalha.
- Se o driver dá o motivo, ele vem junto (endereço e tipo da falha).
- Se a GPU não termina um quadro em 10 s, conta como o mesmo erro (o driver às vezes reinicia sem avisar o programa).
- Mande o relatório quando o editor perguntar na próxima abertura: com o passe, o conserto é bem mais rápido. [Relatar um bug](article:report-bug)
- Enquanto isso: atualize o driver e tente um preset mais leve (Configurações > Médio).
--- en
The graphics card stopped in the middle of a frame and the driver reset it. The editor saves the scene (Emergency save) and writes a report.
- The report says **in which pass the GPU stopped** ("The GPU stopped at frame N in “tecido (simulacao)”"): every pass of the frame is marked while the GPU works.
- When the driver gives its reason, it comes along (the fault's address and kind).
- A frame the GPU doesn't finish in 10 s counts as the same error (the driver sometimes resets without telling the program).
- Send the report when the editor asks the next time it opens: with the pass, the fix is much faster. [Report a bug](article:report-bug)
- Meanwhile: update the driver and try a lighter preset (Settings > Medium).
