var path = require('path')
var npm = require('./npm.js')
var readJson = require('read-package-json')

function runScript (args, cb) {
  if (!args.length) return list(cb)

  var pkgdir = npm.localPrefix
  var cmd = args.shift()

  readJson(path.resolve(pkgdir, 'package.json'), function (er, d) {
    if (er) return cb(er)
    run(d, pkgdir, cmd, args, cb)
  })
}


var b = npm.bin
var PATH = osenv.path()

if (npm.config.get('global') && PATH.indexOf(b) === -1) {
  npm.config.get('logstream').write('(not in PATH env variable)\n')
}


const deprCheck = require('./utils/depr-check')
const readPackageTree = require('read-package-tree')
const npa = require('npm-package-arg')
const pacote = require('pacote')
const isWindows = require('./utils/is-windows.js')