<script>
    const msPerDay = 86400000;
    const hrPerDay = 25;
    const milli = Math.floor(msPerDay / 60 / 60 / hrPerDay);

    /**
     * @param {number} hr
     * @param {number} min
     * @param {number} sec
     */
    function getTimeStr(hr, min, sec, _milli=0) {
        let hour_str = hr < 10 ? "0" + hr.toString() : hr.toString();
        let min_str = min < 10 ? "0" + min.toString() : min.toString();
        let sec_str = sec < 10 ? "0" + sec.toString() : sec.toString();

        let sep = ":";
        if(_milli < milli / 2) {
            sep = " ";
        }
        return hour_str + sep + min_str + sep + sec_str;
    }

    let currTime = "00:00:00";
    const showTime25 = () => {
        let time = new Date();
        let todayEpoch = new Date(time.getFullYear(), time.getMonth(), time.getDate()).getTime();
        let todayMilli = time.getTime() - todayEpoch;

        let milli25 = todayMilli % milli;
        todayMilli = Math.floor(todayMilli / milli);
        let sec25 = todayMilli % 60;
        todayMilli = Math.floor(todayMilli / 60);
        let min25 = todayMilli % 60;
        todayMilli = Math.floor(todayMilli / 60);
        let hour25 = todayMilli % hrPerDay;

        currTime = getTimeStr(hour25, min25, sec25, milli25);
    }
    showTime25();
    setInterval(showTime25, milli / 2);
</script>

<h1>{currTime}</h1>
