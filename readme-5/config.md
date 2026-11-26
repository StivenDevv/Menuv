# Config

```lua
Config = Config or {}

-- Language Selection: 'en' | 'es' | 'fr' | 'de' | 'pt' | 'it'
Config.Language = 'en'

-- Framework Selection: 'ESX' | 'QB' | 'STANDALONE'
Config.Framework = 'QB'

-- Database Provider: 'oxmysql' | 'mysql-async' | 'ghmattimysql'
Config.Database = 'oxmysql'

-- Debug mode for console logging
Config.Debug = false

-- =============================================
-- COMMANDS CONFIGURATION
-- =============================================
Config.ReportCommand             = 'report'
Config.AdminReportCommand        = 'reports'
Config.NotificationToggleCommand = 'rn'

-- =============================================
-- GENERAL SETTINGS
-- =============================================
Config.UseSteamNames                = false
Config.SaveRespondedReports         = true
Config.TeleportBackAfterConcluding  = true
Config.NewReportNotifyType          = 'STANDALONE'
Config.LatestSendNotifyToAdmin      = true
Config.GetAllPlayersForNotify       = false
Config.AllowMultipleGOTO            = false
Config.PersistReports               = true

-- Function to initialize config locales
function Config.Setup()
    Config.NoAdminAssistingText = Locales['no_admin_assisting']

    Config.ReportCategoriesTranslation = {
        player   = Locales['cat_player'],
        bug      = Locales['cat_bug'],
        question = Locales['cat_question'],
    }

    Config.CommandSuggestions = {
        ['report']            = { text = Locales['cmd_report_suggestion']     },
        ['adm_report']        = { text = Locales['cmd_adm_report_suggestion'] },
        ['adm_notifications'] = { text = Locales['cmd_adm_notif_suggestion']  },
    }

    Config.Notifications = {
        ['success_rep']       = { title = Locales['notif_title_report'],      text = Locales['notif_success_rep'],       time = 5000, type = 'success' },
        ['adm_answered']      = { title = Locales['notif_title_report'],      text = Locales['notif_adm_answered'],      time = 5000, type = 'info'    },
        ['player_answered']   = { title = Locales['notif_title_report'],      text = Locales['notif_player_answered'],   time = 5000, type = 'info'    },
        ['adm_assist']        = { title = Locales['notif_title_report'],      text = Locales['notif_adm_assist'],        time = 5000, type = 'info'    },
        ['rep_concluded']     = { title = Locales['notif_title_report'],      text = Locales['notif_rep_concluded'],     time = 5000, type = 'success' },
        ['rep_canceled']      = { title = Locales['notif_title_report'],      text = Locales['notif_rep_canceled'],      time = 5000, type = 'error'   },
        ['adm_rep_concluded'] = { title = Locales['notif_title_report'],      text = Locales['notif_adm_rep_concluded'], time = 5000, type = 'success' },
        ['new_rep']           = { title = Locales['notif_title_new_report'],  text = Locales['notif_new_rep'],           time = 8000, type = 'info'    },
        ['rep_not_on']        = { title = Locales['notif_title_report'],      text = Locales['notif_rep_not_on'],        time = 5000, type = 'success' },
        ['rep_not_off']       = { title = Locales['notif_title_report'],      text = Locales['notif_rep_not_off'],       time = 5000, type = 'error'   },
        ['rep_not_exist']     = { title = Locales['notif_title_report'],      text = Locales['notif_rep_not_exist'],     time = 5000, type = 'error'   },
        ['rep_loaded']        = { title = Locales['notif_title_reports'],     text = Locales['notif_rep_loaded'],        time = 5000, type = 'info'    },
    }
end
```
