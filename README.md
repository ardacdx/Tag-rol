client.on("userUpdate", async (oldUser, newUser) => {
  if (oldUser.username !== newUser.username) {
    let tag = "!"; //tagınız
    let sunucu = "712978502176997380"; //sunucu ID
    let kanal = "718761514542301237" //log kanal id
    let rol = "752891156102250517"; //tag alınca verilcek rol id
    if (newUser.username.includes(tag) && !client.guilds.cache.get(sunucu).members.cache.get(newUser.id).roles.cache.has(rol)) {
      client.channels.cache.get(kanal).send(`${newUser} **\`${tag}\`** tagını aldığı için <@&${rol}> rolünü kazandı!`)
      client.guilds.cache.get(sunucu).members.cache.get(newUser.id).roles.add(rol)
    } if (!newUser.username.includes(tag) && client.guilds.cache.get(sunucu).members.cache.get(newUser.id).roles.cache.has(rol)) {
      client.guilds.cache.get(sunucu).members.cache.get(newUser.id).roles.remove(rol)
      client.channels.cache.get(kanal).send(`${newUser} **\`${tag}\`** tagını çıkardığı için <@&${rol}> rolünü kaybetti!`)
    }

  }
})
