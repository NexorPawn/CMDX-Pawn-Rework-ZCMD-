# CMDX-Pawn-Rework-ZCMD-
A new command processor is being created for pawn samp, based on zcmd

CMDX - This is a stable and extensible command processor for SA-MP, built on zcmd with an emphasis on simplicity, macros, and alias support.

> Creator: **Nexor**
> Version: **v1.0.1 Actual (2025)**  
> Based on ZCMD, rewritten and improved

**Features**

Alias support
Macro syntax: CMD:name(playerid, params[])
Flexible parameter parsing — no need for SSCANF
Easy to integrate
No extra dependencies


**Installation**

>1. Download the include file.
>2. Extract it into the pawno/includes/ > folder.
>3. Then add the new include to your mod: **<cmdx>**

> Note: Disable SSCANF, as this include/plugin provides similar functionality built-in — just under a different function name.

There are some small errors as this is a test version, I know about some errors and improvements, errors need to be fixed, I will definitely fix them and release a new update!)

Also write what can be corrected, improved, and added. 

https://github.com/NexorPawn/CMDX-Pawn-Rework-ZCMD-/releases/tag/v1.0.1-beta


**How to Use CMDX Command Processor (v1.0.1 Beta)**  



Hey there! 👋 If you're looking for an easy way to handle commands in SA-MP with aliases and clean parsing, here's a quick guide to get you started with **CMDX**.  



### **Installation**  

Just drop `cmdx.inc` into your `pawno/includes` folder and add this to your script:  

```pawn

#include <cmdx>
```  

### **Creating Commands**  

Use `CMD:` (or `COMMAND:`) to define a new command. Example:  
```pawn

CMD:hello(playerid, params[]) 
{
    SendClientMessage(playerid, -1, "Hello, world!");
    return 1;
}
```  

### **Adding Aliases (Shortcuts)**  

Want `/hi` or `/yo` to do the same as `/hello`? Easy!  
```pawn

// Single alias:
CMDX_AddAlias("hi", "hello");  
// Or use the macro (shorter version):
ALIAS("yo", "hello");  
```  
Now, `/hi`, `/yo`, and `/hello` will all work the same way!  

### **Parsing Arguments**  

Need to split command arguments? Use `CMDX_Parse`:  
```pawn

CMD:givecash(playerid, params[]) 
{
    new args[2][64]; // Stores 2 arguments (max 64 chars each)
    new count = CMDX_Parse(params, args, 2, 64);  

    if(count < 2) 
    {
        SendClientMessage(playerid, -1, "Usage: /givecash [playerid] [amount]");
        return 1;
    }  

    new targetid = strval(args[0]);
    new amount = strval(args[1]);

    GivePlayerMoney(targetid, amount);
    SendClientMessage(playerid, -1, "Money sent!");
    return 1;
}

```   

### **Available Macros**  

For quick alias setups, use these shortcuts:  
```pawn
ALIAS("pm", "msg");      // /pm = /msg  
ALS("h", "help");        // /h = /help  
AL("plus", "add");       // /plus = /add 

```  

### **⚠️ Important Notes**  

- This is a **beta version**! 🚧 Some bugs might exist.  
- If a command doesn’t work, check `print()` or server logs for errors.  
- Report issues on GitHub so we can improve it!  

### **🔗 Useful Examples**  

- **Private Message System** (`/pm [id] [text]`)  
- **Math Command** (`/add [num1] [num2]`)  
- **Debug Tool** (`/echo [text]` – repeats your args)  
Check the full demo in `cmdx.pwn` for more!  

**🚀 Ready to try?**  
Download, test, and let me know what you think! Feedback = faster improvements.  


