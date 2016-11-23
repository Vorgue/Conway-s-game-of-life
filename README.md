# Conway-s-game-of-life
Array.prototype.checkNeighbours = function (i,j,n,m) {
	var count = 0;
	console.log(this);
	var bor = (i === 0);
	var eor = (i === (n - 1));
	var boc = (j === 0);
	var eoc = (j === (m - 1));
	console.log(bor, eor, boc, eoc);
	if (!(bor) && !(boc)) count += this[i-1][j-1];
	if (!(bor)) count += this[i-1][j];
	if (!(bor) && !(eoc)) count += this[i-1][j+1];
	if (!(eoc)) count += this[i][j+1];
	if (!(eor) && !(eoc)) count += this[i+1][j+1];
	if (!(eor)) count += this[i+1][j];
	if (!(eor) && !(boc)) count += this[i+1][j-1];
	if (!(boc)) count += this[i][j-1];
	console.log(count);
	return count
}

liveOrDie = function (count, value) {
	var res = 0;
	if (count < 2) res = 0;
	if (count == 2) res = value;
	if (count == 3) res = 1;
	if (count > 3) res = 0;
	return res
}

function nextGen (cells) {
  if (cells == '') return []'
	var n = cells.length;
	var m = cells[0].length;
	var result = new Array(n);
	for (var i = 0; i < n; i++) {
		result[i] = new Array(m)
	}
	for (var i = 0; i < n; i++) {
		for (var j = 0; j < n; j++) {
			result[i][j] = liveOrDie( cells.checkNeighbours(i,j,n,m) , cells[i][j] )
		}
	}
	return result
}
